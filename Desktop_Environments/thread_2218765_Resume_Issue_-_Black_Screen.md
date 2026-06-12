---
title: "Resume Issue - Black Screen"
date: 2014-04-21
forum: Desktop Environments
---

### Post by Jay_N on 2014-04-21
I'm haivng trouble with 'resume'. My computer will suspend fine but when I touch a key to resume, everything seems to turn on but the screen remains black. The back light comes on for the screen but nothing else.
I've searched everywhere and can't find a solution.
I've tried the following code and then when trying to suspend it would just go to the login screen.

```
Create the **/etc/pm/sleep.d/20_custom-ehci_hcd** file:


 $ sudo touch /etc/pm/sleep.d/20_custom-ehci_hcd

 [B]
Open the newly created file:[/B]

 
$ gksudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd


``` ```
[B]
Paste this script:[/B]

 #!/bin/sh
VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1
unbindDev() {
echo -n > $DEV_LIST 2>/dev/null
for driver in $DRIVERS; do
DDIR=$DRIVERS_DIR/${driver}_hcd
for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
echo -n "$dev" > $DDIR/unbind
echo "$driver $dev" >> $DEV_LIST
done
#for bus in $EHCI_BUSES; do
echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/unbind
# done
done
}
bindDev() {
if [ -s $DEV_LIST ]; then
while read driver dev; do
DDIR=$DRIVERS_DIR/${driver}_hcd
#for bus in $EHCI_BUSES; do
echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/bind
#done
while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
echo -n "$dev" > $DDIR/bind
if [ ! -L "$DDIR/$dev" ]; then
sleep $BIND_WAIT
else
break
fi
MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
done
done < $DEV_LIST fi rm $DEV_LIST 2>/dev/null
chvt 1
chvt 7
}
EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
case "$1" in
hibernate|suspend)
unbindDev;;
resume|thaw)
bindDev;;
esac

```
```
[B]
Set 755 permissions on the script:[/B]

 $ sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd

```

If anyone has had this problem and has a solution, It would be greatly appreciated.

---

### Post by lukas-o on 2014-04-22
Hi, 

I've started ubuntu with an older kernel (3.11.0-19-generic) and it seemed to work, now it resumes from suspention correctly.
Hope it will be fixed soon.

---

### Post by kurt18947 on 2014-04-22
I've seen the same symptom during development but the problem is usually fixed by the time a version is released.  I've been doing research on suspending via the command line and have come across some possible fixes.  I haven't tried anything as I don't have the 'resume with a black screen' problem on any machine right now.  I see the problem on a machine with an nVidia Geforce 210 video card.  Using the proprietary nVidia driver seems to help.  

Here is a thread which discusses the issue, post #8 & #9.

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/blank-screen-after-resume-from-suspend-764822/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/blank-screen-after-resume-from-suspend-764822/)

---

### Post by Jay_N on 2014-04-27
I've updated my NVIDIA drivers and that fixed the issue. Their updated driver had a fix for the suspend black screen issue.

---

