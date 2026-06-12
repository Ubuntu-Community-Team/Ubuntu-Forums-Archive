---
title: "HOWTO: Run a Program or Windows Screen Saver when System is Idle"
date: 2009-01-03
forum: General Help
---

### Post by Streeterer on 2009-01-03
First, create a perl scipt

```
sudo gedit  /usr/local/sbin/SCRIPTNAME.pl

```
Then, paste and edit this script to include the commands you wish to run. Replace COMMAND with the desired command. LEAVE THE QUOTATION MARKS

```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
#when Ubuntu idles these commands will run
system("COMMAND");
system("COMMAND"); #you can remove or add more commands by adding another system("COMMAND"); line
} elsif (m/^\s+boolean false/) {
#when Ubuntu returns from idle these commands will run, delete these two system lines if not wanted/needed
system("COMMAND");
system("COMMAND");
}
}


```

Save the file.

Next, allow the script to be run:

```
sudo chmod +x /usr/local/sbin/SCRIPTNAME.pl
```


Add the script to the Sessions manager (System>Preferences>Sessions) so that it starts with your login using this command:

```
perl /usr/local/sbin/SCRIPTNAME.pl
```

To use a Windows screensaver, Wine must be installed. To install the PolarClock Screensaver, for example, download it ([http://blog.pixelbreaker.com/downloads/polarclock/PolarClock3_win.zip](http://blog.pixelbreaker.com/downloads/polarclock/PolarClock3_win.zip)) and run the .exe. Then create a new command in the Perl Script in the "runs when idles" section that points to the PolarClock3.scr file. (Currently my favorite screensaver)

```
wine /home/YOURUSERNAME/.wine/dosdevices/c:/windows/system32/PolarClock3.scr

```

Go to System>Preferences>Screensaver and set your idle time. DISABLE "Activate screensaver when computer is idle"

The script for just running the PolarClock Screensaver would looks like this:

```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
system("wine /home/YOURUSERNAME/.wine/dosdevices/c:/windows/system32/PolarClock3.scr");
}
}


```


Thats all there is to it!

---

### Post by Dirjel on 2009-01-15
All right, this is interesting.  Here's how I set mine up:
```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
#when Ubuntu idles these commands will run
system("mirage -R -s /home/dirjel/Pictures");
} elsif (m/^\s+boolean false/) {
#when Ubuntu returns from idle these commands will run, delete these two system lines if not wanted/needed
system("killall mirage")}}
```

It launches Mirage in random slideshow mode showing every picture I have saved into my Pictures folder.  That part works fine.

The "elsif" thing doesn't work, though.  I tried "killall mirage," but that didn't do anything.  I also tried "killall -9 mirage," because that's what I have to use to kill any stray rejoystick daemons, but that didn't work either, in this case.

Am I doing something wrong, or is it a problem with the code?  It's not really a HUGE deal to have to manually close Mirage after the screensaver kicks in, but I'd rather not do it if I don't have to.

---

### Post by hyper_ch on 2009-01-15
HOWTOs must be posted in the tutorials section so it can first be reviewed by the staff.

---

### Post by Streeterer on 2009-01-15
To run a kill command on a program that this script starts, you need to add an & to the end of the command. 

```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
system("mirage -f -R -s /home/dirjel/Pictures **&**");
} elsif (m/^\s+boolean false/) {
system("killall mirage");
}
}
```

This should work fine for you.

---

### Post by Dirjel on 2009-01-16
Sweet, dude, it works perfect! :D

I don't know much of anything about scripting or anything, so I appreciate the help.

---

### Post by Streeterer on 2009-01-16
All that the & does is run the command in the background and free the terminal for other tasks. Without it, the "hidden" terminal in which the script is running is not freed to run the killall command until Mirage is closed, which is obviously not helpful :)

---

### Post by uzd4ce on 2009-09-24
I'm trying to use this script to dismount any Truecrypt volumes when the screensaver is activated.

So I have the command set up as "truecrypt -d" and it appears to run, but apparently it needs the admin password to dismount.

How can I tweak the script so that it runs as root?

Thanks

---

### Post by Steve_54 on 2009-11-01
Nice script. Mine quit working with 9.10. I changed member='SessionIdleChanged' to member='ActiveChanged' and now it works again.

Steve

---

### Post by Perkins on 2010-12-25
> **uzd4ce said:**
> I'm trying to use this script to dismount any Truecrypt volumes when the screensaver is activated.

So I have the command set up as "truecrypt -d" and it appears to run, but apparently it needs the admin password to dismount.

How can I tweak the script so that it runs as root?

Thanks


Lazy way would be to stick it in your system's rc.local instead of the user's session startup list.

---

### Post by äxl on 2012-03-10
As written here ([external link]("http://www.narf.ssji.net/%7Eshtrom/wiki/projets/gnomescreensavernosession")) idleness depends on Gnome Session since 2009-01-18. So you have to change the original perl script like this:

```

#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.SessionManager.Presence',member='StatusChanged'\"";

open (IN, "$cmd |");

while (<IN>)
{
    if (m/^\s+uint32 3/)
    {
        #when Ubuntu idles these commands will run
        system("COMMAND");
        system("COMMAND"); #you can remove or add more commands by adding another system("COMMAND"); line
    }
    elsif (m/^\s+uint32 0/)
    {
        #when Ubuntu returns from idle these commands will run, delete these two system lines if not wanted/needed
        system("COMMAND");
        system("COMMAND");
    }
}

```Note changes in line 2, 8 and 14.

---

