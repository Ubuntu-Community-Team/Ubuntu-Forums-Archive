---
title: "Backup to tape drive (hp dat 72) - Which software?"
date: 2010-07-05
forum: Desktop Environments
---

### Post by anivio on 2010-07-05
Hi!

I am a Ubuntu 10.04 Desktop user.

I am searching for a backup software to backup to my hp dat72 tape drive. It is only to backup my data from 1 PC.

I have already found bacula but it seems to big for my purpose. I need an easy and automatic software.

Could you recommend a backup software for my needs?

Thank you.

anivio

---

### Post by lukeiamyourfather on 2010-07-05
I'd try [this]("http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/") plus cron. Cheers!

---

### Post by mmerlone on 2010-07-05
Depends on your needs, but I'd suggest bacula. Enterprise grade.

---

### Post by lsutiger on 2010-07-05
Wouldn't backintime work as long as it is a mounted drive? Very simple and light.
[http://www.le-web.org/back-in-time/](http://www.le-web.org/back-in-time/)

Also in the repositories.

---

### Post by lukeiamyourfather on 2010-07-06
> **lsutiger said:**
> Wouldn't backintime work as long as it is a mounted drive? Very simple and light.
[http://www.le-web.org/back-in-time/](http://www.le-web.org/back-in-time/)

Also in the repositories.

The original poster is asking about a ***tape*** drive. Nearline is different because the system doesn't care what the endpoint is and doesn't have to do anything like rewind tapes. I think Bacula supports some tape drives. Cheers!

---

### Post by anivio on 2010-07-06
Hi!

Thanks a lot for your help.

I have tried the solution which lukeiamyourfather has posted. It works but if i backup 20 GB it needs a lot of time to display the list of files on the tape backup. Thats because the drive is only a slow dat72 one.

EDIT: Maybe the logfile includes a list of backed up files. I will have a look.

I am a new ubuntu/linux user and bacula seems to have a very difficult configuration. The manual has over 600 sites.

At the moment i am not sure which solution i should use. Maybe the configuration of bacula will give me a lot of experience. 

Thank you

anivio

---

### Post by anivio on 2010-07-06
```
[COLOR=#808080]*#!/bin/bash*[/COLOR]
[COLOR=#808080]*# A UNIX / Linux shell script to backup [COLOR=#7A0874]**dirs**[/COLOR] to tape device like /dev/st0 [COLOR=#7A0874]**(**[/COLOR]linux[COLOR=#7A0874]**)**[/COLOR]*[/COLOR]
[COLOR=#808080]*# This script [COLOR=#C20CB9]**make**[/COLOR] both full and incremental backups.*[/COLOR]
[COLOR=#808080]*# You need at two sets of five  tapes. Label each tape [COLOR=#C20CB9]**as**[/COLOR] Mon, Tue, Wed, Thu and Fri.*[/COLOR]
[COLOR=#808080]*# You can run script at midnight or early morning each day using cronjons.*[/COLOR]
[COLOR=#808080]*# The operator or sys admin can replace the tape every day after the script has [COLOR=#000000]**done**[/COLOR].*[/COLOR]
[COLOR=#808080]*# Script must run [COLOR=#C20CB9]**as**[/COLOR] root or configure permission via [COLOR=#C20CB9]**sudo**[/COLOR].*[/COLOR]
[COLOR=#808080]*# -------------------------------------------------------------------------*[/COLOR]
[COLOR=#808080]*# Copyright [COLOR=#7A0874]**(**[/COLOR]c[COLOR=#7A0874]**)**[/COLOR] [COLOR=#000000]1999[/COLOR] Vivek Gite <vivek@nixcraft.com>*[/COLOR]
[COLOR=#808080]*# This script is licensed under GNU GPL version [COLOR=#000000]2.0[/COLOR] or above*[/COLOR]
[COLOR=#808080]*# -------------------------------------------------------------------------*[/COLOR]
[COLOR=#808080]*# This script is part of nixCraft shell script collection [COLOR=#7A0874]**(**[/COLOR]NSSC[COLOR=#7A0874]**)**[/COLOR]*[/COLOR]
[COLOR=#808080]*# Visit http://bash.cyberciti.biz/ [COLOR=#000000]**for**[/COLOR] [COLOR=#C20CB9]**more**[/COLOR] information.*[/COLOR]
[COLOR=#808080]*# -------------------------------------------------------------------------*[/COLOR]
[COLOR=#808080]*# Last updated on : March[COLOR=#000000]-2003[/COLOR] - Added log [COLOR=#C20CB9]**file**[/COLOR] support.*[/COLOR]
[COLOR=#808080]*# Last updated on : Feb[COLOR=#000000]-2007[/COLOR] - Added support [COLOR=#000000]**for**[/COLOR] excluding files / [COLOR=#7A0874]**dirs**[/COLOR].*[/COLOR]
[COLOR=#808080]*# -------------------------------------------------------------------------*[/COLOR]
[COLOR=#007800]LOGBASE=[/COLOR]/root/backup/log
 
[COLOR=#808080]*# Backup [COLOR=#7A0874]**dirs**[/COLOR]; [COLOR=#000000]**do**[/COLOR] not prefix /*[/COLOR]
[COLOR=#007800]BACKUP_ROOT_DIR=[/COLOR][COLOR=#FF0000]"home sales"[/COLOR]
 
[COLOR=#808080]*# Get todays day like Mon, Tue and so on*[/COLOR]
[COLOR=#007800]NOW=[/COLOR]$[COLOR=#7A0874]**(**[/COLOR][COLOR=#C20CB9]**date**[/COLOR] +[COLOR=#FF0000]"%a"[/COLOR][COLOR=#7A0874]**)**[/COLOR]
 
[COLOR=#808080]*# Tape devie name*[/COLOR]
[COLOR=#007800]TAPE=[/COLOR][COLOR=#FF0000]"/dev/st0"[/COLOR]
 
[COLOR=#808080]*# Exclude file*[/COLOR]
[COLOR=#007800]TAR_ARGS=[/COLOR][COLOR=#FF0000]""[/COLOR]
[COLOR=#007800]EXCLUDE_CONF=[/COLOR]/root/.backup.exclude.conf
 
[COLOR=#808080]*# Backup Log file*[/COLOR]
[COLOR=#007800]LOGFIILE=[/COLOR][COLOR=#007800]$LOGBASE[/COLOR]/[COLOR=#007800]$NOW[/COLOR].backup.log
 
[COLOR=#808080]*# Path to binaries*[/COLOR]
[COLOR=#007800]TAR=[/COLOR]/bin/[COLOR=#C20CB9]**tar**[/COLOR]
[COLOR=#007800]MT=[/COLOR]/bin/mt
[COLOR=#007800]MKDIR=[/COLOR]/bin/[COLOR=#C20CB9]**mkdir**[/COLOR]
 
[COLOR=#808080]*# ------------------------------------------------------------------------*[/COLOR]
[COLOR=#808080]*# Excluding files when using tar*[/COLOR]
[COLOR=#808080]*# Create a [COLOR=#C20CB9]**file**[/COLOR] called [COLOR=#007800]$EXCLUDE_CONF[/COLOR] using a text editor*[/COLOR]
[COLOR=#808080]*# Add files matching patterns such [COLOR=#C20CB9]**as**[/COLOR] follows [COLOR=#7A0874]**(**[/COLOR]regex allowed[COLOR=#7A0874]**)**[/COLOR]:*[/COLOR]
[COLOR=#808080]*# home/vivek/iso*[/COLOR]
[COLOR=#808080]*# home/vivek/*.[COLOR=#C20CB9]**cpp**[/COLOR]~*[/COLOR]
[COLOR=#808080]*# ------------------------------------------------------------------------*[/COLOR]
[COLOR=#7A0874]**[**[/COLOR] -f [COLOR=#007800]$EXCLUDE_CONF[/COLOR] [COLOR=#7A0874]**]**[/COLOR] && [COLOR=#007800]TAR_ARGS=[/COLOR][COLOR=#FF0000]"-X $EXCLUDE_CONF"[/COLOR]
 
[COLOR=#808080]*#### Custom functions #####*[/COLOR]
[COLOR=#808080]*# Make a full backup*[/COLOR]
full_backup[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**{**[/COLOR]
	[COLOR=#7A0874]**local**[/COLOR] [COLOR=#007800]old=[/COLOR]$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**pwd**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
	[COLOR=#7A0874]**cd**[/COLOR] /
	[COLOR=#007800]$TAR[/COLOR] [COLOR=#007800]$TAR_ARGS[/COLOR] -cvpf [COLOR=#007800]$TAPE[/COLOR] [COLOR=#007800]$BACKUP_ROOT_DIR[/COLOR]
	[COLOR=#007800]$MT[/COLOR] -f [COLOR=#007800]$TAPE[/COLOR] rewind
	[COLOR=#007800]$MT[/COLOR] -f [COLOR=#007800]$TAPE[/COLOR] offline
	[COLOR=#7A0874]**cd**[/COLOR] [COLOR=#007800]$old[/COLOR]
[COLOR=#7A0874]**}**[/COLOR]
 
[COLOR=#808080]*# Make a  partial backup*[/COLOR]
partial_backup[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**{**[/COLOR]
	[COLOR=#7A0874]**local**[/COLOR] [COLOR=#007800]old=[/COLOR]$[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**pwd**[/COLOR][COLOR=#7A0874]**)**[/COLOR]
	[COLOR=#7A0874]**cd**[/COLOR] /
	[COLOR=#007800]$TAR[/COLOR] [COLOR=#007800]$TAR_ARGS[/COLOR] -cvpf [COLOR=#007800]$TAPE[/COLOR] -N [COLOR=#FF0000]"$(date -d '1 day ago')"[/COLOR] [COLOR=#007800]$BACKUP_ROOT_DIR[/COLOR]
	[COLOR=#007800]$MT[/COLOR] -f [COLOR=#007800]$TAPE[/COLOR] rewind
	[COLOR=#007800]$MT[/COLOR] -f [COLOR=#007800]$TAPE[/COLOR] offline
	[COLOR=#7A0874]**cd**[/COLOR] [COLOR=#007800]$old[/COLOR]
[COLOR=#7A0874]**}**[/COLOR]
 
[COLOR=#808080]*# Make sure all [COLOR=#7A0874]**dirs**[/COLOR] exits*[/COLOR]
verify_backup_dirs[COLOR=#7A0874]**(**[/COLOR][COLOR=#7A0874]**)**[/COLOR][COLOR=#7A0874]**{**[/COLOR]
	[COLOR=#7A0874]**local**[/COLOR] [COLOR=#007800]s=[/COLOR][COLOR=#000000]0[/COLOR]
	[COLOR=#000000]**for**[/COLOR] d [COLOR=#000000]**in**[/COLOR] [COLOR=#007800]$BACKUP_ROOT_DIR[/COLOR]
	[COLOR=#000000]**do**[/COLOR]
		[COLOR=#000000]**if**[/COLOR] [COLOR=#7A0874]**[**[/COLOR] ! -d /[COLOR=#007800]$d[/COLOR] [COLOR=#7A0874]**]**[/COLOR];
		[COLOR=#000000]**then**[/COLOR]
			[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#FF0000]"Error : /$d directory does not exits!"[/COLOR]
			[COLOR=#007800]s=[/COLOR][COLOR=#000000]1[/COLOR]
		[COLOR=#000000]**fi**[/COLOR]
	[COLOR=#000000]**done**[/COLOR]
	[COLOR=#808080]*# [COLOR=#000000]**if**[/COLOR] not; just die*[/COLOR]
	[COLOR=#7A0874]**[**[/COLOR] [COLOR=#007800]$s[/COLOR] -eq [COLOR=#000000]1[/COLOR] [COLOR=#7A0874]**]**[/COLOR] && [COLOR=#7A0874]**exit**[/COLOR] [COLOR=#000000]1[/COLOR]
[COLOR=#7A0874]**}**[/COLOR]
 
[COLOR=#808080]*#### Main logic ####*[/COLOR]
 
[COLOR=#808080]*# Make sure log [COLOR=#C20CB9]**dir**[/COLOR] exits*[/COLOR]
[COLOR=#7A0874]**[**[/COLOR] ! -d [COLOR=#007800]$LOGBASE[/COLOR] [COLOR=#7A0874]**]**[/COLOR] && [COLOR=#007800]$MKDIR[/COLOR] -p [COLOR=#007800]$LOGBASE[/COLOR]
 
[COLOR=#808080]*# Verify dirs*[/COLOR]
verify_backup_dirs
 
[COLOR=#808080]*# Okay [COLOR=#7A0874]**let**[/COLOR] us start backup procedure*[/COLOR]
[COLOR=#808080]*# If it is monday [COLOR=#C20CB9]**make**[/COLOR] a full backup;*[/COLOR]
[COLOR=#808080]*# For Tue to Fri [COLOR=#C20CB9]**make**[/COLOR] a partial backup*[/COLOR]
[COLOR=#808080]*# Weekend no backups*[/COLOR]
[COLOR=#000000]**case**[/COLOR] [COLOR=#007800]$NOW[/COLOR] [COLOR=#000000]**in**[/COLOR]
	Mon[COLOR=#7A0874]**)**[/COLOR]	full_backup;;
	Tue|Wed|Thu|Fri[COLOR=#7A0874]**)**[/COLOR] 	partial_backup;;
	*[COLOR=#7A0874]**)**[/COLOR] ;;
[COLOR=#000000]**esac**[/COLOR] > [COLOR=#007800]$LOGFIILE[/COLOR] [COLOR=#000000]2[/COLOR]>&[COLOR=#000000]1[/COLOR]

```

I have made a backup.sh file with the above code. I have tried to execute the script (with sudo) but it does not start. I have tried the original script and a script with customized lines.

Whats wrong?

---

### Post by lukeiamyourfather on 2010-07-06
I have some experience with bash scripting but I guess not enough to recognize the problem outright. Starting from the first step, how is it being launched? Does the shell return anything? Cheers!

---

### Post by anivio on 2010-07-07
I have tried to launch the script via a terminal. First the original one and second one with customized lines for the logbase and the backup dirs. I have not made a exclude file.

Steps:

1) Change into the directory where the script is located
2) Start the script via "sudo bash backup.sh" or via "sudo sh backup.sh"
3) Nothing happend. No output. Only a logfile without entries

Also i have tried to launch the script via crontab. Also this does not work.

I have tried the following script [https://help.ubuntu.com/8.04/serverguide/C/backups-shellscripts-rotation.html#backup-shellscript-tapedrive](https://help.ubuntu.com/8.04/serverguide/C/backups-shellscripts-rotation.html#backup-shellscript-tapedrive)

This one works fine, but i have no logfile outputs.

---

