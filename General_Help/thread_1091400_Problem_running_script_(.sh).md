---
title: "Problem running script (.sh)"
date: 2009-03-09
forum: General Help
---

### Post by balboa41 on 2009-03-09
Hi.  I am kind of newbie at running scripts, but I have run some of then without problems.  Actually, though, I am having problems running a script that makes backups of Virtual Machines on an ESXi Server, from an Ubuntu Client.  

When I run the script, this is the result:

jrivera@UbuntuBKPServer:~/Desktop$ sudo sh esxi_backup.sh
: not found.sh: 33:
: not found.sh: 45:
: not found.sh: 46:
esxi_backup.sh: 66: Syntax error: word unexpected (expecting "do")

However, this is the script on line 66 and some others (note that it does says "do"):(:

for i in $( vmware-cmd -H $HOSTNAME -U $USERNAME -P $PWD -l ); do
        VM_DIR=$(dirname "$i")
        VM_NAME=$(basename "$VM_DIR")
        echo "["$(basename "$VM_DIR")"]" | tee -a $LOG

I need to solve this problem in order to make my backups, as this script looks interesting, because I don't have to pay a LOT of money in order to make the VM's backups.

Any suggestion will be totally appreciated!

---

### Post by ddrichardson on 2009-03-10
My scripting is pretty rusty but I think you need:
```
for i in $(vmware-cmd -H $HOSTNAME -U $USERNAME -P $PWD -l)
do
    VM_DIR=$(dirname "$i")
    VM_NAME=$(basename "$VM_DIR")
    echo "["$(basename "$VM_DIR")"]" | tee -a $LOG
done
```

---

### Post by balboa41 on 2009-03-11
Thanks for the reply, ddrichardson.  Anyway, I found another script, much better than this one, that made the work without any problem.  If any of you out there are trying to accomplish this, get the ghettoVCB.sh.  It will let you make backup of your Virtual Machines in a ESXi host.  It works great!!!

Actually, I am making backups to another host that is using NFS on Ubuntu Server 8.04.  :D

---

