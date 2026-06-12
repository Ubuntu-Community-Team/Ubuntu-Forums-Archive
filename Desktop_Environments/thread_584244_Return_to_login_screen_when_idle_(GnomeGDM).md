---
title: "Return to login screen when idle (Gnome/GDM)"
date: 2007-10-20
forum: Desktop Environments
---

### Post by tonyisntcreative on 2007-10-20
After some terrible (usual) Windows antics on our family computer, I've taken it upon myself to introduce my family to Linux, and save us all a ton of hassle.  They seem to be fine with the switch since pretty much all of the things they do are done the same way (they're internet browsers, and that's pretty much it).

For the last few  years we've been using Windows XP under a single user.  I thought about using a single user with the new install, but I think it'd just be a better idea to give us all separate accounts.  Being that my mom and brother are totally foreign to any other operating system, and that they have never been in the habit of logging out when they leave the computer (they've never needed to when we had it setup to use one account), people sitting down at the computer after someone else had used it and having to be under their name won't be very uncommon.

I've been trying to figure out of there is a way that I can make Gnome switch back to the login screen when the session goes idle, after 10 minutes or so.  I'd prefer that it didn't log the user out, since my brother often keeps AIM on for long amounts of time, or is using BitTorrent, and I don't want to kill the programs.  If after 10 minutes the computer could automatically "switch users," or just return to the GDM screen, this problem would be solved.  I figure this could be as easy as executing "gdmflexiserver," but I don't know how to make this exec when the computer goes idle.

Linked [here](http://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#head-ac43c8f33bc700a5e298e6a82ded0e8bb9b33043) I've found what looks to be the beginning of a solution, but it's incomplete.  This is what it says:
> **Is there a way to perform actions when the screensaver activates or deactivates? Or when the session becomes idle?**
One way is to watch for the D-Bus signals from gnome-screensaver. Here's an example of how to perform actions when the session becomes idle or is no longer idle:
```
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    if (m/^\s+boolean true/) {
        print "*** Session is idle ***\n";
    } elsif (m/^\s+boolean false/) {
        print "*** Session is no longer idle ***\n";
    }
}
```
It looks like it might be as easy as putting "gdmflexiserver" in the line where it says "Session is idle," but I have no idea what file this is referencing.

I've also thought of setting each account to lock the screen when the computer goes idle, so there will at least be a "Switch User" button.  This is only a semi-alternative, but it's still not exactly what I want.  Along these lines, another idea was to figure out if I could somehow switch the default "Lock Screen" command from what it is&#8212;'gnome-screensaver -l'&#8212;simply to 'gdmflexiserver.'  This would also achieve what I want.  

But maybe there is another solution, and if anyone knows how to achieve I'd be very glad to hear it.  

So again, this is what I want done: I want to make it so my family computer switches back to the GDM login screen when the computer goes idle so people aren't constantly sitting down logged in as the wrong user.

---

### Post by tonyisntcreative on 2007-10-21
Bump.

---

### Post by tonyisntcreative on 2007-10-23
Darn.  Nobody knows?  I hate to say it, but Windows does it.

---

### Post by Izkata on 2008-02-24
> **tonyisntcreative said:**
> It looks like it might be as easy as putting "gdmflexiserver" in the line where it says "Session is idle," but I have no idea what file this is referencing.

Granted this is a rather old post, but as I found it by Google...

```
izkata@Izz:~$ which gdmflexiserver 
/usr/bin/gdmflexiserver
```

I just tested it in gnome-terminal, and running it with no arguments appears to effectively do a "switch user".

---

