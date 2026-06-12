---
title: "/tmp doesn't get emptied on reboot"
date: 2010-10-16
forum: Desktop Environments
---

### Post by greenmang0 on 2010-10-16
I have noticed that my /tmp doesn't get emptied on reboot. Currently the oldest file in /tmp is dated 27th Aug 2010. I have to empty /tmp manually or else it keeps on bulging.

Here's the ls output of /tmp - [http://sprunge.us/KJGD](http://sprunge.us/KJGD)

I have TMPTIME=0 in /etc/default/rcS.

What can be the reason? I have been upgrading Kubuntu since 8.04. Currently running Maverick 10.10

Any help will be appreciated.

pksadiq at irc.freenode.net on #ubuntu told me to put rm -rf /tmp/* in /etc/rc.local

But it's a workaround. What can be the reason that TMPTIME=0 is
going unnoticed?

---

### Post by Zorael on 2010-10-18
Hmm. /tmp contents is deleted by the **/etc/init/mounted-tmp.conf** script. Perhaps something is wrong in the logic there.

```
# mounted-tmp - Clean /tmp directory
#
# Cleans up the /tmp directory when it does not exist as a temporary
# filesystem.

description	"Clean /tmp directory"

start on mounted MOUNTPOINT=/tmp
env MOUNTPOINT=/tmp

task

script
    . /etc/default/rcS

    cd "${MOUNTPOINT}"
    rm -f .X*-lock

[B]    [COLOR="Green"]case "${TMPTIME}" in
        -*|infinite|infinity)
	    exit 0
	    ;;
    esac[/COLOR]

[COLOR="RoyalBlue"]    if [ "${TMPTIME}" = "0" -o -z "${TMPTIME}" ]
    then
	TEXPR=""
	DEXPR=""
    else
	TEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME} -atime +${TMPTIME}"
	DEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME}"
    fi
[/COLOR][/B]
    EXCEPT='! -name .
            ! ( -path ./lost+found -uid 0 )
            ! ( -path ./quota.user -uid 0 )
            ! ( -path ./aquota.user -uid 0 )
            ! ( -path ./quota.group -uid 0 )
            ! ( -path ./aquota.group -uid 0 )
            ! ( -path ./.journal -uid 0 )
            ! ( -path ./.clean -uid 0 )
            ! ( -path "./...security*" -uid 0 )'

    # Remove all old files, then all empty directories
[B][COLOR="Red"]    find . -depth -xdev $TEXPR $EXCEPT ! -type d -delete
    find . -depth -xdev $DEXPR $EXCEPT -type d -empty -delete[/COLOR][/B]
end script
```

**[COLOR="Green"]Green section[/COLOR]**: So if the $TMPTIME variable is negative, infinite or infinity, the script will stop right away.

**[COLOR="RoyalBlue"]Blue section[/color]**: If $TMPTIME is 0 or undefined, it will empty /tmp contents except for the files/directories listed in the $EXCEPT variable. 
+ *Additionally*, if $TMPTIME is anything else (defined and above 0), it will define some extra constraints so only files/directories created, modified or(/and?) accessed within the last $TMPTIME hours will be deleted. (If I understand the manpage of find correct.)

Everything *should* be fine, as you say set $TMPTIME=0 in **/etc/default/rcS**, but obviously something is not right. I would add some logging statements so you know that the script is executed, and how far into it it actually gets. Sort of like the following, with added lines in **[COLOR="Purple"]purple[/COLOR]**;
```
# mounted-tmp - Clean /tmp directory
#
# Cleans up the /tmp directory when it does not exist as a temporary
# filesystem.

description	"Clean /tmp directory"

start on mounted MOUNTPOINT=/tmp
env MOUNTPOINT=/tmp

task

script
    [B][COLOR="Purple"]LOGFILE=/var/tmp/tmp.log
    echo "mounted-tmp script started at $(date)" >> $LOGFILE[/color][/b]

    . /etc/default/rcS

    cd "${MOUNTPOINT}"
    rm -f .X*-lock

[B]    [COLOR="Green"]case "${TMPTIME}" in
        -*|infinite|infinity)
            echo "green section caused script exit" >> $LOGFILE
	    exit 0
	    ;;
    esac[/COLOR]

[COLOR="RoyalBlue"]    if [ "${TMPTIME}" = "0" -o -z "${TMPTIME}" ]
    then
        [COLOR="Purple"]echo "blue section says TMPTIME is 0 or undefined ($TMPTIME)" >> $LOGFILE[/COLOR]
	TEXPR=""
	DEXPR=""
    else
        [COLOR="purple"]echo "blue section went haywire! ($TMPTIME)" >> $LOGFILE[/COLOR]
	TEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME} -atime +${TMPTIME}"
	DEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME}"
    fi
[/COLOR][/B]
    EXCEPT='! -name .
            ! ( -path ./lost+found -uid 0 )
            ! ( -path ./quota.user -uid 0 )
            ! ( -path ./aquota.user -uid 0 )
            ! ( -path ./quota.group -uid 0 )
            ! ( -path ./aquota.group -uid 0 )
            ! ( -path ./.journal -uid 0 )
            ! ( -path ./.clean -uid 0 )
            ! ( -path "./...security*" -uid 0 )'

    # Remove all old files, then all empty directories
[B][COLOR="Red"]    find . -depth -xdev $TEXPR $EXCEPT ! -type d -delete
    find . -depth -xdev $DEXPR $EXCEPT -type d -empty -delete[/COLOR][/B]
    **[COLOR="purple"]echo "done deleting, script finished" >> $LOGFILE[/COLOR]**
end script
```

Then check **/var/tmp/tmp.log** and see if it has anything interesting to say. Perhaps the script isn't being run at all, for some reason, in which case the log file will simply not exist.

---

### Post by greenmang0 on 2010-10-21
Thanks for the reply.

echo "blue section says TMPTIME is 0 or undefined ($TMPTIME)" >> $LOGFILE


This is the last line I get in /var/tmp/tmp.log

That means script doesn't get executed past that line.

What can be the reason?

---

### Post by Zorael on 2010-10-21
Let's add some more debugging lines, then.
```
*[...]*

[b][COLOR="RoyalBlue"]    if [ "${TMPTIME}" = "0" -o -z "${TMPTIME}" ]
    then
        [COLOR="Purple"]echo "blue section says TMPTIME is 0 or undefined ($TMPTIME)" >> $LOGFILE[/COLOR]
	TEXPR=""
	DEXPR=""
    else
        [COLOR="purple"]echo "blue section went haywire! ($TMPTIME)" >> $LOGFILE[/COLOR]
	TEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME} -atime +${TMPTIME}"
	DEXPR="-mtime +${TMPTIME} -ctime +${TMPTIME}"
    fi
[/COLOR]
    [COLOR="purple"]echo "now defining EXCEPT" >> $LOGFILE[/COLOR][/b]
    EXCEPT='! -name .
            ! ( -path ./lost+found -uid 0 )
            ! ( -path ./quota.user -uid 0 )
            ! ( -path ./aquota.user -uid 0 )
            ! ( -path ./quota.group -uid 0 )
            ! ( -path ./aquota.group -uid 0 )
            ! ( -path ./.journal -uid 0 )
            ! ( -path ./.clean -uid 0 )
            ! ( -path "./...security*" -uid 0 )'

    # Remove all old files, then all empty directories
    [b][COLOR="purple"]echo "running first find command" >> $LOGFILE[/COLOR]
[COLOR="Red"]    find . -depth -xdev $TEXPR $EXCEPT ! -type d -delete
    [COLOR="purple"]echo "running second find command" >> $LOGFILE[/COLOR]
    find . -depth -xdev $DEXPR $EXCEPT -type d -empty -delete[/COLOR]
    [COLOR="purple"]echo "done deleting, script finished" >> $LOGFILE[/COLOR][/B]
end script
```
Also, could you attach your mounted-tmp.conf? So we can be sure that it's identical to mine (which works).

---

### Post by greenmang0 on 2010-10-22
[http://pastebin.com/dxBzEEUZ](http://pastebin.com/dxBzEEUZ)

It's identical to yours...

---

### Post by greenmang0 on 2010-10-23
mounted-tmp script started at Sat Oct 23 10:22:30 IST 2010
TMPTIME is 0 or undefined (0)
now defining EXCEPT
running first find command


This is what I got in /var/tmp/tmp.log

---

### Post by Zorael on 2010-10-25
Try reenacting it. Create a script containing that snippet, save it someplace and set it as executable.

```
#!/bin/bash

cd /tmp

EXCEPT='! -name .
	! ( -path ./lost+found -uid 0 )
	! ( -path ./quota.user -uid 0 )
	! ( -path ./aquota.user -uid 0 )
	! ( -path ./quota.group -uid 0 )
	! ( -path ./aquota.group -uid 0 )
	! ( -path ./.journal -uid 0 )
	! ( -path ./.clean -uid 0 )
	! ( -path "./...security*" -uid 0 )'

echo "running first find command"
sudo find . -depth -xdev $TEXPR $EXCEPT ! -type d -delete
echo "running second find command"
sudo find . -depth -xdev $DEXPR $EXCEPT -type d -empty -delete
echo "done deleting, script finished"
```

Log out, hit Ctrl+Alt+F1 to hop to a tty, then stop X with '**sudo stop kdm**' (or gdm if you're using that). Then run the script and see what it says.

You can always to '**sudo start kdm**' again to start X back up.

---

### Post by greenmang0 on 2010-10-27
ok... this executable worked perfectly... removing all the stuff in /tmp

then why doesn't this block work in /etc/init/mounted-tmp.conf?

Mystery!!!

---

### Post by greenmang0 on 2010-10-27
I put this line
find / -maxdepth 1 >> $LOGFILE
after
echo "mounted-tmp script started at $(date)" >> $LOGFILE
line.
And I got only one line in $LOGFILE which was

"mounted-tmp script started at Wed Oct 27 12:35:51 IST 2010"

That implies mounted-tmp.conf doesn't execute find command.

Then I put the absolute path of find command /usr/bin/find ... no luck.

Then echo $(which find) again no luck
Then I put
alias search=find
search / -maxdepth 1 >> $LOGFILE

no luck again

Why doesn't script execute find command?

---

### Post by greenmang0 on 2010-10-27
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/587995](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/587995)

Here's what I found... it's a bug

copying /usr/bin/find to /bin/ is the workaround for it... but there should be a proper solution

---

### Post by greenmang0 on 2010-10-27
Solved

Thanks [Zorael]("http://ubuntuforums.org/member.php?u=266856")

---

