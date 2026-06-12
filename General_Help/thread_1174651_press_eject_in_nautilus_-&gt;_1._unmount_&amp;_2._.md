---
title: "press eject in nautilus -&gt; 1. unmount &amp; 2. spin down / turn off: HOW?"
date: 2009-05-31
forum: General Help
---

### Post by omg! on 2009-05-31
jaunty seems to be really cool. i've put it on a persistent live usb-stick and since i don't use the main hard drive in my laptop anymore i want to turn it off manually whenever i'm not using it.

what i imagine to be most comfortable is to press the eject button in nautilus and it first unmounts the partition(s) and then turns the drive off / spins it down.

google hasn't revealed any instructions for accomplishing this, so i'd like to ask you guys. any help would be greatly appreciated.

i would also welcome instructions for similar methods to unmount and spin down, e.g. not necessarily involving the eject button.

---

### Post by dcstar on 2009-05-31
> **omg! said:**
> jaunty seems to be really cool. i've put it on a persistent live usb-stick and since i don't use the main hard drive in my laptop anymore i want to turn it off manually whenever i'm not using it.

what i imagine to be most comfortable is to press the eject button in nautilus and it first unmounts the partition(s) and then turns the drive off / spins it down.

google hasn't revealed any instructions for accomplishing this, so i'd like to ask you guys. any help would be greatly appreciated.

i would also welcome instructions for similar methods to unmount and spin down, e.g. not necessarily involving the eject button.
Make adjustments as necessary:
```
#!/bin/sh
/sbin/hdparm -y /dev/sdb
```
or:
```
#!/bin/bash
#
# Script to spin down external drives after "X" seconds
# Usage: sudo ./scsi-idle 1500 (for 25 minutes + sleepval)
#
# Requires sg3-utils package
#

declare -a DID
declare -a DSTATUS
declare -a DTIME
declare -a DOFF

interval=$1
sleepval=120
buspath=/sys/bus/scsi/devices

while [ true ]; do
thetime=`date +%s`

for scsidev in $( ls --format=across $buspath ); do
   if devenum="$( ls ${buspath}/${scsidev} | grep 'block:' )"; then
      devdir=$buspath/$scsidev/$devenum
      read devsize < ${devdir}/size
      read devremove < ${devdir}/removable

      if [ $devremove -eq 0 ] && [ $devsize -gt 0 ]; then # device is the right type
         read newstat < ${devdir}/stat
         hhit=0; listlen=${#DID[@]}  #; echo $listlen $scsidev

         for ((i=0;i<$listlen;i++)); do
            if [ ${DID[$i]} = $scsidev ]; then
               if [ "${DSTATUS[$i]}" = "$newstat" ]; then
                  if [ $[ ${thetime} - ${DTIME[$i]} ] -ge $interval ] \
                  && [ ${DOFF[$i]} -eq 0 ]; then
                   # sg_start --pc=5 /dev/${devenum:6} # put into sleep mode
                     sg_start --stop /dev/${devenum:6} # alternate method
                     echo stop /dev/${devenum:6}
                     DTIME[$i]=$thetime
                     DOFF[$i]=1
                  fi
               else
                  DSTATUS[$i]=$newstat
                  DTIME[$i]=$thetime
                  DOFF[$i]=0
               fi
               hhit=1; break
            fi
         done
         if [ $hhit -eq 0 ]; then   # add new drive to watch list
            DID[$listlen]=$scsidev
            DSTATUS[$listlen]=$newstat
            DTIME[$listlen]=`date +%s`
            DOFF[$listlen]=0
         fi
      fi
   fi
done
sleep $sleepval
done
```

---

