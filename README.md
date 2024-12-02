This README documents the process of creating, managing, and deleting Pluggable Databases (PDBs) in Oracle Database 19c.

## Environment
- Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
- Version 19.3.0.0.0

## Operations Performed

### 1. Creating PDB: plsql_class2024db

```sql
CREATE PLUGGABLE DATABASE plsql_class2024db
ADMIN USER an_plsqlauca IDENTIFIED BY Password123
FILE_NAME_CONVERT = (
    'C:\APP\ORADATA\ORCL\PDBSEED\SYSTEM01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\plsql_class2024db\SYSTEM01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\SYSAUX01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\plsql_class2024db\SYSAUX01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\UNDOTBS01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\plsql_class2024db\UNDOTBS01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\TEMP',
    'C:\oracle19c\oradata\ORCL2\orclpdb\plsql_class2024db\TEMP'
);
```

### 2. Creating PDB: an_to_delete_pdb

```sql
CREATE PLUGGABLE DATABASE an_to_delete_pdb
ADMIN USER an_plsqlauca IDENTIFIED BY Password123
FILE_NAME_CONVERT = (
    'C:\APP\ORADATA\ORCL\PDBSEED\SYSTEM01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\an_to_delete_pdb\SYSTEM01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\SYSAUX01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\an_to_delete_pdb\SYSAUX01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\UNDOTBS01.DBF',
    'C:\oracle19c\oradata\ORCL2\orclpdb\an_to_delete_pdb\UNDOTBS01.DBF',
    'C:\APP\ORADATA\ORCL\PDBSEED\TEMP',
    'C:\oracle19c\oradata\ORCL2\orclpdb\an_to_delete_pdb\TEMP'
);
```

### 3. Verifying PDB Creation

```sql
SHOW PDBS;
SELECT PDB_ID, PDB_NAME, STATUS, CON_ID FROM DBA_PDBS;
```

### 4. Unplugging PDB: an_to_delete_pdb

```sql
ALTER PLUGGABLE DATABASE an_to_delete_pdb UNPLUG INTO 'C:\App\admin\orcl\dpdump\an_to_delete_pdb.xml';
```

### 5. Dropping PDB: an_to_delete_pdb

```sql
DROP PLUGGABLE DATABASE an_to_delete_pdb INCLUDING DATAFILES;
```

## Results

- Successfully created two PDBs: `plsql_class2024db` and `an_to_delete_pdb`
- Verified PDB creation using `SHOW PDBS` and `SELECT` from `DBA_PDBS`
- Successfully unplugged and dropped `an_to_delete_pdb`



This README provides a quick reference for the PDB operations performed, including creation, verification, and deletion processes in Oracle Database 19c.



