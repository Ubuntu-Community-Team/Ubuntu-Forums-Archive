---
title: "Fax to modem over network?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-11-27
Im wondering if I can send a fax to a modem on another machine over a network?

I have a home server and like it to be the hub of my network. Lots of things run through it. So Im wondering if I put a modem in it is their any software that I can send a fax to it from another PC? Clients are Ubuntu based and the server is XP Pro based. 

Im thinking about moving the server to linux but I have to learn more 1st. :)

---

### Post by bluetoad on 2005-11-27
My fax server is on Ubuntu so that is different to your setup.

I have a script I call from OpenOffice.org. Look for fax in the OpenOffice.org help and it will point you at the spadmin command.  Use spadmin to add the fax as
a printer.  Make sure you put the arguments (PHONE) and (TMP).

e.g. /usr/local/bin/remfax.sh (PHONE)  (TMP)

When you print to the fax printer you have added, OpenOffice.org will ask for the fax number.

The script basically uses ssh to copy the files to be faxed to the server and then runs the required command on the server to queue the fax.  (I use mgetty so faxspool is called).

It is possible to set up an ssh server on an XP box.  I have done so in the past using cygwin ([www.cygwin.com)](www.cygwin.com)).  You'll have a better idea of how to access the software on that machine.  This is just an idea that works for me.

Here are some of the key ideas from the script (it is is rough and needs tidying up - I've chopped out my debug statements etc for brevity)

#!/bin/sh
REMOTE_FAX=yourServer
REMOTE_TMPDIR=/tmp/

faxArgs=""

if [ $1 = "-n" ]
then
   faxArgs="$faxArgs $1"
   shift
fi

phoneNumber=$1
shift

scp -p $* $REMOTE_FAX:$REMOTE_TMPDIR 2>&1 >/dev/null

faxFiles=""
for f in $*
do
   baseFile=`basename $f`
    faxFiles="$faxFiles $baseFile"
done

(ssh $REMOTE_FAX "cd $REMOTE_TMPDIR; faxspool $faxArgs $phoneNumber $faxFiles )& 2>&1 >/dev/null

exit 0

---

### Post by MetalMusicAddict on 2005-11-27
Thanx man. Ill look into this. Anyone else?

---

