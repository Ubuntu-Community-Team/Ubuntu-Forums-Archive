---
title: "How to system-wide cron crontab schedule for now"
date: 2009-04-10
forum: General Help
---

### Post by directcharitycontribution on 2009-04-10
Most important anything is to set correct for you 'environment variables' -- so edit system crontab to read this below as follows;

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

# SHELL=/bin/sh
# PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

SHELL=/bin/bash
# PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/username/bin
# MAILTO=username
# HOME=/home/username
DISPLAY=:0.0
#EDITOR=editoruchose

(basically u have add line 'DISPLAY=:0.0')

[http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)
[http://ubuntuforums.org/tags.php?tag=crontab](http://ubuntuforums.org/tags.php?tag=crontab) better read marked as [SOLVED]!

=====================

=====================

=====================


like cask-scheduler for people of micro$ort this work for some useful rubbish rubbish rubbish computers box.

it is system-wide crontab working via "sudo gedit /etc/crontab" While this editing is going on, quite absorbing, you may find optional convenience put "sudo gedit /etc/crontab"  'application in terminal' shortcut launcher on panel and for regular editing setting up temporarily set nopasswd for "sudo gedit /etc/crontab" in sudoers file (see [http://ubuntuforums.org/showthread.php?t=680312&highlight=sudoers+nopasswd](http://ubuntuforums.org/showthread.php?t=680312&highlight=sudoers+nopasswd)). (nopasswd may also be necessary for some commands you want called with crontab).

so the first thing i did wanted to set up switched media-streaming. while partially working with streams can optimise housework, baths, snoozing or other non-puter multi-tasking and time-shifting playbacks and off-peak isp rates. as most broadcasts end hourly i set killall on the hour and restarts after news/intros. don't wanna listen that over again.

( you should want create a userdumb, without any permissions or content and instant screenlocks, that can runs mode ummonitored or autoboots from alarm without any security compromise.)
(you for such convenience CAN instead to REDESIGN crontab just duplicate crontabs lines for any usersname (other than root) modes, everybody mode (like player) can same then you remove some! but less IS more!!)

these may not be ideals solution, but start works now and easy copy-paste develop when any other crontabs/scripts process comes along makes more sophisticated
putting # before line disables that cron entry or description. very useful eg. leave commands setup for various contingencies, oneoffs, short-notice varying schedules decisions or testing.

and it looks this. (YOU KEEP YOUR EXISTING ROOT COMMANDS AND REPLACE OTHER COMMANDS WITH YOUR CHOICES AND USERSNAME)

-------------------------------------------------------------------------------------
system-wide crontab is as BETWEEN lines below

[http://ubuntuforums.org/showthread.php?t=1123807](http://ubuntuforums.org/showthread.php?t=1123807)
-------------------------------------------------------------------------------------
backgroun info collects see post here [http://ubuntuforums.org/showthread.php?t=943621](http://ubuntuforums.org/showthread.php?t=943621)

---

