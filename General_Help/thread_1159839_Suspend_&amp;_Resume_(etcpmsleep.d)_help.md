---
title: "Suspend &amp; Resume (/etc/pmsleep.d) help"
date: 2009-05-15
forum: General Help
---

### Post by mizunoX on 2009-05-15
I've just discovered /etc/pm/sleep.d and am trying to create a script based on examples that I've seen on the internet, but the resume portion of it doesn't seem to work.

Here it is:
> #!/bin/bash                                             
LOG="/var/log/xbmcsuspend.log"                          

. /usr/lib/pm-utils/functions

case "$1" in
        suspend|hibernate)
                date=`date`
                echo "$date : suspend/hibernate" >>$LOG          
                killall xbmc.bin                       
                killall irexec                     
                ;;                                     
        resume|thaw)                                   
                date=`date`                            
                echo "$date : resume/thaw" >>$LOG   
                su user -c "irexec -d &"
                su user -c "/usr/share/xbmc/xbmc.bin &"
                ;;
        *)
                ;;
esac

exit $?

It's supposed to close xbmc and irexec before suspending, and it does, but when resuming it adds the comment to the log, but doesn't relaunch irexec or xbmc.  Is there something obvious that I'm doing wrong in those lines where I'm calling irexec and xbmc?
As I said before, I'm new to this so any help would be appreciated.
Thanks

---

