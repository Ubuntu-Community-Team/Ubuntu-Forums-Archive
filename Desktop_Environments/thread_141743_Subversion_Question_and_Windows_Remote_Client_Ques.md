---
title: "Subversion Question and Windows Remote Client Question"
date: 2006-03-08
forum: Desktop Environments
---

### Post by Boiler98 on 2006-03-08
Hello all.  (I hope this is the correct forum for these types of questions)

I am installing **Subversion** as a server to replace a small fileserver currently serving the purpose.  I installed the 'subversion', 'subversion-tools' packages, and all required packages, through Synaptic but am a little lost as to what happened.

I was hoping for a nifty GUI to let me set things up, letting me really set the server up beyond my limited knowledge of the command line interface.  Can anyone else who has Subversion installed help me to understand what was installed (if anything) in terms of server admin?  Do the packages only include the command line interface or is there something more?

It was a bummer not to find a new "Subversion" entry in one of my menus.

I noticed a "Portable Apache" module was installed, but I'm not sure why.  Was it just installed for the database maintenance, or is it a full web server package that will allow me to access the repository over http?  I'm just not clear on what has been installed for what purpose to know what to focus on in the Subversion documentation.

Connecting to **Windows** is my next goal.  I would like to get a remote client running so I can unplug my CRT from the Ubuntu box and just tuck the box in the corner.  Can someone suggest a Windows application that would allow me to do this?

Thanks for any input!

---

### Post by RAOF on 2006-03-09
The subversion packages are entirely command line based.  And subversion isn't a general file server - it's a version-control system.  It's not clear you know this - it'd be a bit of a surprise if you didn't know :)

As for a brief howto on SVN, there's the homepage [http://subversion.tigris.org/](http://subversion.tigris.org/).  But the command line tools you're after are **svnadmin** and **svnserve**.  Typing **svnadmin help** will give you a list of commands, and **svnadmin help *foo*** will give you help for the command [i]foo[/b].

Basically, you want to create a repository with the svnadmin program, and then start a svn server serving that repository.

If you put this code into a file /etc/init.d/svnserved, mark the file executable, and run sysv-rc-conf (you may have to install it using synaptic) to add "svnserved" to your boot sequence.
```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/svnserve
NAME=svnserve
DESC="SVN Repository Server Daemon"

test -x $DAEMON || exit 0

OPTIONS="-d -r /var/local/Repository"

# Get lsb functions
. /lib/lsb/init-functions
. /etc/default/rcS

start() {
        log_begin_msg "Starting $DESC... "
        #       echo "Starting $DESC: "
        if ! start-stop-daemon --start --quiet --oknodo --exec $DAEMON -- $OPTIONS
 >/dev/null 2>&1; then
                status=$?
                log_end_msg $status
                return $status
        fi
        log_end_msg 0
        return 0
}

case "$1" in
  start)
        start
        ;;
  stop)
        log_begin_msg "Stopping $DESC: "
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        log_end_msg $?
        ;;
  restart|force-reload)
        $0 stop
        sleep 1
        start
        #echo "$NAME."
        ;;
  *)
        N=/etc/init.d/$NAME
        log_success_msg "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

---

### Post by Boiler98 on 2006-03-09
Thanks RAOF.  I do know SVN is a version control system - I have it running already, just moving servers. :)  Much thanks for the script too, my current server has me restarting the deamon after a reboot - it will be nice not doing that now. :cool:

---

### Post by Boiler98 on 2006-03-09
[QUOTE=RAOF]If you put this code into a file /etc/init.d/svnserved, mark the file executable, and run sysv-rc-conf (you may have to install it using synaptic) to add "svnserved" to your boot sequence.[/QUOTE]

RAOF, where can I find the 'sysv-rc-conf' application?  It does not appear in a system wide 'find' and I can't seem to find it in Synaptic -- if I did a search for 'sysv' I get a hit for 'sysv-rc' (which is installed) but no '...-conf'.

Thank you again!

---

### Post by RAOF on 2006-03-09
I think you could also try "BUM" (the Boot Up Manager) - that's a GUI application to do the same thing.

---

### Post by jezjones on 2006-03-10
I hope this is still on topic...

With the recent install of subversion we are finding that it does not deal with conflicts very well. Two people have edited a CSS file. They have been working at different points in the file and whenever we try and put it back into subversion it fails with a conflict.

It may be a verison control system but it is making collaborative work a nightmare... so much so we are thinking of rolling back to source safe because so far manually dealing with conflicts has wasted alot of time.

Am i using it wrong or is it just not intended to do this... and if not i dont see the point of it.


Jez

---

### Post by cwaldbieser on 2006-03-11
[QUOTE=jezjones]I hope this is still on topic...

With the recent install of subversion we are finding that it does not deal with conflicts very well. Two people have edited a CSS file. They have been working at different points in the file and whenever we try and put it back into subversion it fails with a conflict.

It may be a verison control system but it is making collaborative work a nightmare... so much so we are thinking of rolling back to source safe because so far manually dealing with conflicts has wasted alot of time.

Am i using it wrong or is it just not intended to do this... and if not i dont see the point of it.


Jez[/QUOTE]

It is a different kind of workflow.  When you work on small projects with only a few developers, VSS gets the job done, but it is not very feature rich, and you can't really ask it to do something like revert back to last Friday's build so you can apply a critical bugfix for a customer without introducing this weeks' untested features.

Conflicts will occur if 2 or more people are working on the same file simultaneously.  If they are different parts of the file, you should just be able to update, and SVN will merge (G) the changes for you automatically.  If it was on the same part of the same file, the developers need to talk to each other about what they want to do.  If you are using Windows clients, TortoisSVN has a pretty good merge tool built in, but I like using WinMerge as an external merge tool instead (it allows editing as you merge which is sometimes useful).

If you find that the people keep working on the same parts of the same files all the time, this might be indicative of a problem where the devs should just get together and actually talk out how they want to proceed (e.g. "OK, you work on the HTML and I will do style sheets today.").

SVN also supports file locking, but the industry seems to be moving away from that for larger projects.  From what I've seen of the new MS Team System, it looks like they are also encouraging moving to a Copy-Modify-Merge workflow.

---

### Post by Boiler98 on 2006-03-13
[QUOTE=RAOF]I think you could also try "BUM" (the Boot Up Manager) - that's a GUI application to do the same thing.[/QUOTE]
Thanks RAOF... at the risk of sounding like a complete dolt - where do I find BUM?

I did another system search and tried searching for it in the application installer with no luck.

Thanks.

**EDIT**
I believe I've found the solution using 'update-rc.d'.  I'll find out for sure when I get the chance to work on the server a little more and boot it back up in a day or two. :)

---

