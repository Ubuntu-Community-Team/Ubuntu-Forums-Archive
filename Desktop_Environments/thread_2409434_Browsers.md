---
title: "Browsers"
date: 2019-01-02
forum: Desktop Environments
---

### Post by sam_w2 on 2019-01-02
I've installed 14.04 LTS onto an old Compaq Presario 2100 and I cannot get any browser like Ubuntu Software Center, Firefox to not crash. 
I've read that Firefox requires SSE2 and this machine only has SSE. However, Firefox does not crash when running the LiveCD on this machine.

ping google.com returns a result.
curl [http://google.com](http://google.com) returns an expected result.
audo apt-get update returns expected output.

```
firefox --safe-mode
``` 
enables the browser to stay up, but crashes when I attempt to visit "http://www.google.com/". The crash reporter does not offer any clues that I can see.

Clicking Ubuntu Software Center in Desktop initially returned a dialog to check my Internet connection.

```
sudo software-center
```
provides some useful info.

```
2019-01-02 17:00:34,194 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
2019-01-02 17:00:34,764 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2019-01-02 17:00:38,207 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2019-01-02 17:00:38,759 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2019-01-02 17:00:38,804 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2019-01-02 17:00:38,892 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2019-01-02 17:00:38,892 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2019-01-02 17:00:39,457 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
```

The error I see is something aout typelib for LaunchpadIntegration. The searches for this error suggest a login problem which thankfully I do not have.

What should I be checking to help isolate the cause?

---

### Post by Frogs Hair on 2019-01-02
14.04 reaches end of life in April 2019 , so I would suggest installing Ubuntu 18.04 . With old hardware consider Lubuntu, Xubuntu, or Ubuntu Mate.

---

### Post by sam_w2 on 2019-01-02
I see I failed to indicate in the post (other than the tag) that I installed Xubuntu xcfe. That would help.

I would agree, but installing anything past Xubuntu 14 either never got started or never finished. This is as close as I've gotten on this machine.

---

### Post by Frogs Hair on 2019-01-02
Running or attempting to run graphical applications using sudo can cause the application to be owned by root. Please use the following ```
sudo -H  [COLOR=#000000][FONT=&amp]software-center[/FONT][/COLOR]
``` For older releases ```
gksu software-center
```

Do you have enough memory run newer browsers ?

---

### Post by sam_w2 on 2019-01-02
Perhaps, but if I was able to browse running on the Live CD would it not hold that I should be able to on the local HD? Note that this is still a near-pristine install. Only installed curl and vim so far.
gksu is not installed, but sudo is.
Running software-center with the -H flag returned the same result as above.
Restarted and Software Center in the desktop "System program problem detected" What little of the stack trace I got suggested "GStreamer" as a problem.
Searching that term with Xubuntu 14 suggested that running 
```
[COLOR=#777777][FONT=monospace]parole --xv false
```
[/FONT][/COLOR]might help with that problem. Restarted and the System program problem detected returned more helpful errors.
One thing I noted was the suggestion that I have obsolete package versions installed notably software-center, app-install-data, etc. 
I did run sudo apt-get update after install but let's run
```
sudo apt-get update
sudo apt-get upgrade
```

I see "Failed to fetch [http://ug.archive.ubuntu.com/](http://ug.archive.ubuntu.com/) ".... "Size mismatch" for nearly all. 
My searches for this phrase returned results for "Hash Sum mismatch" but nothing for "Size mismatch"
This suggests that while curl, ping work, perhaps the system is not connecting to the internet.

ifconfig returns a valid IP on eth0 and wlan0. As before I can ping google.com and return expected results.

What would you suggest I try next? thx, sam

---

### Post by Frogs Hair on 2019-01-02
You can change the Ubuntu download sever location if you are in fact connected to the Internet and seeing a 404 failed to fetch error. Can you supply some system information cpu,memory, and so on ?

---

### Post by sam_w2 on 2019-01-03
Yes, happily. mobile AMD Athlon 1.65ghz, 704mb ram, 30g HD.
How to change where apt-get pulls from for Xubuntu 14 Trusty Tahr?

---

### Post by sam_w2 on 2019-01-03
Following on the suggestion that apt-get target URI can be changed, I searched and found this:
[https://askubuntu.com/questions/640964/apt-get-where-are-the-sources-stored](https://askubuntu.com/questions/640964/apt-get-where-are-the-sources-stored)

In this case, there is an /etc/apt/apt.conf file which had a proxy. Being a new install, I don't have this conf file, nor do I see any in /etc/apt/apt.conf.d/ that would suggest something is mis-set. But if somehow something like a proxy was injected into the system that could be a cause. But I'm certain that I've used apt-get install, but since this is a fresh install, I've been unable to apt-get upgrade.

---

### Post by Frogs Hair on 2019-01-03
[FONT=Roboto]
[/FONT][FONT=arial][SUB][SIZE=2]If you are running 64 bit you have a memory shortage and even with 32 bit you're close depending what processes are running.

 Recommended Hardware [/SIZE][/SUB][/FONT][SUB][SIZE=2][COLOR=#000000]Firefox 62.0 System Requirements &#8212; Mozilla[/COLOR][/SIZE][/SUB][FONT=arial]
[/FONT][FONT=Roboto]
[LIST]
[*][FONT=arial][SUB][SIZE=2]Pentium 4 or newer processor that supports SSE2.[/SIZE][/SUB][/FONT]
[*][FONT=arial][SUB][SIZE=2]512MB of RAM / 2GB of RAM for the 64-bit version.[/SIZE][/SUB][/FONT]
[/LIST]
[/FONT][FONT=arial]
[/FONT][FONT=Roboto]
[/FONT][FONT=Roboto]
[/FONT]

---

### Post by sam_w2 on 2019-01-11
Yes, your assertions are correct. However, I was trying to resolve why booting from the DVD that Firefox on the same hardware ran fine. 
Then it came to me that when I installed Xubuntu 14 from the DVD that I set it to update the software.

Boot from the DVD:

firefox -v returns 28.0
Ubuntu Software Center 13.10

Boot from the hard drive:
firefox -v returns 64.0
unable to determine what Ubuntu Software Center is running at because it crashes on startup.

Regardless, long term running this machine with software stuck in unsafe versions is untenable and this hardware is EOL as far as browsing the internet goes. 

Which is your overall point, I perceive. Thx for your time, sam

---

### Post by TheFu on 2019-01-12
It could be that using sudo with a GUI created all the setting directories and files with root as the owner inside your normal userid HOME directory.  
Using sudo definitely runs the following process as root, but doesn't change the HOME to be that for the root userid, hence the issue.  This can definitely break other GUI applications trying to access and update their config files as your normal userid.

I'm just guessing that this is the issue.

In short, don't run GUI programs as root.  The programs which need this elevated permissions, should be setup to force it by their menu .desktop configuration file.  If they aren't then use **sudo -H** as a workaround.  From the sudo manpage:
```
     -H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.
```
It is not the default behavior on Ubuntu systems.

Ok, with all that said, what's the fix?  **sudo chown -R sam_w2:sam_w2 ~/** This assumes your userid on the system is sam_w2 and the default group for that useid is also sam_w2.  For typical home users, this should be fine.

And did I mention, don't run GUI programs as root?

---

