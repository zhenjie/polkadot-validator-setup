# Bootstrap a node

1. Create a new server on any VPS and update `hv_inventory.yml` with the new IP address
2. Update `hv_userpassword`
3. Run `ansible-playbook -i hv_setup_inventory.yml  hv_setup_env.yml`

Node should be running ans start sync from block #1

# Restore from a snapshot

Go to https://ksm-rocksdb.polkashots.io/ to find the latest snapshot and checksum, and update following
value in `hv_inventory.yml`,

```
polkadot_db_snapshot_url='https://ksm-rocksdb.polkashots.io/kusama-8590456.RocksDb.7z'
polkadot_db_snapshot_checksum='sha256:490674fabeca344cf153294780e004a52e28e308238ab821078363d87cc09963'
```

Restore with `ansible-playbook -i hv_inventory.yml main_restore_db.yml -K`