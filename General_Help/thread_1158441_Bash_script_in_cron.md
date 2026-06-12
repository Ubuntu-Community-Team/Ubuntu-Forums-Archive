---
title: "Bash script in cron"
date: 2009-05-13
forum: General Help
---

### Post by jamesyp on 2009-05-13
I'm trying to write a bash script for use in cron, to familiarize myself with both of those.  The script is meant to use xplanet to update my desktop background with a planet shot centered on my home town.

```
#!/bin/bash
rm -f /tmp/earth-*.jpg
IMAGE=/tmp/earth-`date +%s`.jpg;
DIR=/home/james/scripts;
xplanet -num_times 1 -output $IMAGE -geometry 1280x800 -longitude -111 -latitude 41;
gconftool -t string -s /desktop/gnome/background/picture_filename $IMAGE;

echo "Script has run" >> $DIR/xplanet.log;
```

If I run the script manually it works fine, but adding it to crontab as
```
* * * * * bash /home/james/scripts/xplanet.sh
```
the background is removed, but the new background is never set.  Interestingly, the final echo line still runs, and the log file is still written to.

Any thoughts on what could be going on?

---

### Post by spiderbatdad on 2009-05-13
sorry I know zilch about bash scripting, but what I believe about crontabs  is tha each line must end in a newline character...Your rm -f line does not appear to, to me.

---

### Post by jamesyp on 2009-05-15
Are you talking about a semi-colon at the end of the rm -f /tmp/earth-*.jpg line?  I added one, but that makes no difference when the script is called from cron.  The background still doesn't update.

---

### Post by KyleBrandt on 2009-05-15
I am not sure, but I would think gconftool edits different settings for different users? When a script is run through cron it doesn't get all the environment variables when you log in.  Maybe trying some environment variables in the script? Particularly DISPLAY and USERNAME

-Kyle

---

### Post by dcstar on 2009-05-15
> **jamesyp said:**
> I'm trying to write a bash script for use in cron, ........
If I run the script manually it works fine
........

Any thoughts on what could be going on?

User environment are **not** cron environments.

Put full paths in all commands and file references.

Anything using X programs needs the X display to be used defined beforehand.

---

### Post by trwww on 2009-05-15
Cron mails errors it has to the owner of the crontab file; run the command [FONT="Courier New"]mail[/FONT] to see if there is anything there.

Also, as others have noted, the environment in a process fired by cron is usually quite different than the environment you have on a desktop.

I ALWAYS use full paths to files and programs and files in my cron scripts. You are most of the way there. I suggest using the full path to [FONT="Courier New"]xplanet[/FONT] and [FONT="Courier New"]gconftool[/FONT].

regards,

---

### Post by FIONEX on 2009-05-16
When are you setting your script to run?

You should set it to run AFTER you login.  Don't use cron for that in my opinion.  Besides, what the hell is  * * * * *.  It's run whenever?
Look under System -> Preferences -> Startup Applications.  It runs a script at every login.

---

### Post by jamesyp on 2009-05-16
FIONEX:  I'm just trying to get cron to run the script in the same way it does when run manually.  The * * * * * asks it to run the script every minute.  I'll change this to every half hour once I can get it working.  If I use the startup programs list, it'll only run the script once at log-in.  Not what I want.

I've changed a few of the lines in the script to:
```
/usr/bin/xplanet -num_times 1 -output $IMAGE -geometry 1280x800 -longitude -111 -latitude 41;
/etc/alternatives/gconftool -t string -s /desktop/gnome/background/picture_filename $IMAGE;
```
using the full paths to xplanet and gconftool.  Cron is calling the script, as I can tell from the lines written to the logfile, but now the background is entirely unmodified.  The original background is never removed.  Before I added absolute paths, the earlier background would get removed, but a new one would not replace it.

As for any environment variables the script needs to preserve, or making the X display user defined, I'm not sure what that means or what I'd do.

Thanks for the help, btw.

---

### Post by llamaX on 2009-05-16
Not sure if it's related to your problem, but does [this post]("http://ubuntuforums.org/showpost.php?p=5996758&postcount=12") help any?

---

### Post by jamesyp on 2009-05-16
LlamaX -- Thanks!  That post did the trick.  Nice to know gconftool needs certain variables to work properly.

---

