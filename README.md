# Monitoring Backuppc with Zabbix

This is based on script found in thread https://www.zabbix.com/forum/showthread.php?t=17273

Tested with Zabbix 2.4 (http://www.zabbix.com/) and Backuppc v3 (http://backuppc.sourceforge.net/).

## Install

1. Add a line from 'sudo' file to your sudo config
2. copy 'zabbix-backuppc.pl' and 'zabbix-discover-backuppc.pl' to '/usr/local/bin'
3. make it executable with backuppc user
4. Import 'backuppc_zbx_export_templates.xml' into Zabbix and configure it

## The template contains

### Backuppc

Information about the BackupPc itself.

#### Items

* BackupPC - Average Backup Speed (Full)
* BackupPC - Average Backup Speed (Incremental)
* BackupPC - BackupPC Process
* BackupPC - BackupPC_dump Process
* BackupPC - BackupPC_link Process
* BackupPC - BackupPC_nightly Process
* BackupPC - Collect Data
* BackupPC - Config Uptime
* BackupPC - Full Backup Count
* BackupPC - Full Backup Size
* BackupPC - Hosts with full age more than 1 week
* BackupPC - Hosts with No backups (2 Days)
* BackupPC - Hosts with No backups (3 Days)
* BackupPC - Hosts with No backups (4 Days)
* BackupPC - Hosts with No backups (5 Days)
* BackupPC - Incremental Backup Count
* BackupPC - Incremental Backup Size
* BackupPC - Jobs (Full Backup)
* BackupPC - Jobs (Incremental Backup)
* BackupPC - Jobs (Other Backup)
* BackupPC - Memory Usage
* BackupPC - Pool Directory Count
* BackupPC - Pool Directory Count (Compressed)
* BackupPC - Pool File Count
* BackupPC - Pool File Count (Compressed)
* BackupPC - Pool File Max Links
* BackupPC - Pool File Max Links (Compressed)
* BackupPC - Pool File Repeat
* BackupPC - Pool File Repeat (Compressed)
* BackupPC - Pool File Repeat Max
* BackupPC - Pool File Repeat Max (Compressed)
* BackupPC - Pool Size
* BackupPC - Pool Size (Compressed)
* BackupPC - Queue (Background)
* BackupPC - Queue (Command)
* BackupPC - Queue (User)
* BackupPC - Uptime
* BackupPC - Version

#### Triggers

* BackupPC - Host without Backups (2 Days)
* BackupPC - Host without Backups (3 Days)
* BackupPC - Host without Backups (4 Days)
* BackupPC - Host without Backups (5 Days)
* BackupPC - Server not Running
* BackupPC - {HOSTNAME} have hosts with full backup older than 1 week

### Backuppc - backups

Discovery from individual backups
- system.run["sudo -u backuppc /usr/local/bin/zabbix-discover-backuppc.pl"]

#### Items

* {#BACKUPHOST} full backup age
* {#BACKUPHOST} full backup BadFile
* {#BACKUPHOST} full backup BadShare
* {#BACKUPHOST} full backup duration
* {#BACKUPHOST} full backup size
* {#BACKUPHOST} full backup tar errors
* {#BACKUPHOST} full backup xfer errors
* {#BACKUPHOST} incremental backup age
* {#BACKUPHOST} incremental backup BadFile
* {#BACKUPHOST} incremental backup BadShare
* {#BACKUPHOST} incremental backup duration
* {#BACKUPHOST} incremental backup size
* {#BACKUPHOST} incremental backup tar errors
* {#BACKUPHOST} incremental backup xfer errors

#### Triggers

* {#BACKUPHOST} has bad file in full backup
* {#BACKUPHOST} has bad file in incremental backup
* {#BACKUPHOST} has bad share in full backup
* {#BACKUPHOST} has bad share in incremental backup
* {#BACKUPHOST} has error in full backup
* {#BACKUPHOST} has error in incremental backup
* {#BACKUPHOST} has tar error in full backup
* {#BACKUPHOST} has tar error in incremental backup
