---
title: "Nautilus doesn't launch"
date: 2011-09-08
forum: Desktop Environments
---

### Post by UltraZone on 2011-09-08
Hi all, I have a problem now where Nautilus won't launch when I click on Places in the top Gnome bar, nor when I click on Shortcuts on the GLX Dock.

It pops up an error dialog box saying: "Could not open location 'file:///home/whateverfolder' No application is registered as handling this file'

What gives?

---

### Post by fdrake on 2011-09-08
> **UltraZone said:**
> Hi all, I have a problem now where Nautilus won't launch when I click on Places in the top Gnome bar, nor when I click on Shortcuts on the GLX Dock.

It pops up an error dialog box saying: "Could not open location 'file:///home/whateverfolder' No application is registered as handling this file'

What gives?

are you using a special effect application like compiz? if so disable it and try if you can open a folder normally. if not try to reinstall nautilus

```

sudo apt-get purge nautilus
sudo apt-get install nautilus
nautilus --check
```

---

### Post by UltraZone on 2011-09-09
I have compiz running of course.

Also, purging Nautilus also removes ubuntu-desktop plus a bunch of other stuff, so this "solution" doesn't work.  

Got anything better suggestions for this problem that doesn't involve breaking my whole computer?

---

### Post by fdrake on 2011-09-09
> **UltraZone said:**
> I have compiz running of course.

Also, purging Nautilus also removes ubuntu-desktop plus a bunch of other stuff, so this "solution" doesn't work.  

Got anything better suggestions for this problem that doesn't involve breaking my whole computer?

my bad, you'r right nautilus has dep with gome-session and ubuntu-desktop
instead of purge did you try --reinstall. also you did not tell us yet if nautilus works when compiz is off.

---

### Post by garvinrick4 on 2011-09-09
> What gives?
Just in case if you right click on Documents or Downloads a directory to be opened by nautilus and then
chose open with and choose file manager and check the box to always open with does it all now open in Nautilus?

---

### Post by Frogs Hair on 2011-09-09
You can reset the default application for opening home folders .
1. Open Nautilus with the computer icon or the terminal .
2. right click on a home folder .
3. Select open with other application.
4. Select file browser from the list .
5. Check remember this application .
6. Test the places menu .

---

### Post by UltraZone on 2011-09-09
Fdrake - marked Nautilus for reinstallation in Synaptic: no good, same problem.

Also, in 11.04 the System setting were shuffled around a bit, now if I go to the Control Center > Appearance there is no "Effects" tab, which I believe used to exist in previous versions of Ubuntu, which had the "No Effects" radio button choice.  Now Compiz is on by default and I'm not really sure how to drop down to Metacity if that is possible.  According to Synaptic Metacity is installed still.

Garvinrick4: I see no such option as "Always open with..." in 11.04, are you running this same version?

Frogs Hair:  tried your suggestions, but there is no option "remember this application"

Oddly Places > Home, Desktop, Docs, etc still don't work.

But, Places > Computer, Network do work.

And odder still is Places > [other partitions where I have Fedora, Windows, etc installed] don't work.  And a Samba share I have bookmarked in Nautilus doesn't work.

All of this is extremely bizarre.... :confused:

---

### Post by mc4man on 2011-09-10
navigate to 
~/.local/share/applications
and delete mimeapps.list

---

### Post by UltraZone on 2011-09-10
Deleted mimeapp.list but it still doesn't work.  Note that a new empty mimeapp.list was created after restart.

Anybody?  I actually moved mimeapp.list to a separate directory, should I edit this file and add some config such that Nautilus works properly?

---

### Post by UltraZone on 2011-09-10
So where is the location of the registration of my home folder default application for handling them?

---

### Post by Krytarik on 2011-09-10
Although the default system wide setting for this should normally take care of that, try adding the below line to the "[Added Associations]" section of your "~/.local/share/applications/mimeapps.list", to look like this:
```
[Added Associations]
inode/directory=nautilus-folder-handler.desktop;
```Hopefully, it works!

---

### Post by UltraZone on 2011-09-14
Krytarik:  I added the line you suggested (it was not already part of the file) but unfortunately it is still not working. :/

---

### Post by UltraZone on 2011-09-15
Hm.

This issue is still not resolved.

Guys what could be going on?  Please help me get to the root of this problem.

Or, is there an alternative to Nautilus that I can use in Gnome 2.32?

---

### Post by Copper Bezel on 2011-09-15
There are a handful of compatible file browsers that you could set as the default, basically any Linux file browser, but if Nautilus runs when you just launch it, but not from the Places menu, then the problem is more likely to be related to the default application. It really seems like fixing the file that Krytarik pointed to should have fixed the issue.

Do you have any desktop environments other than Gnome installed (such as KDE or XFCE?) That sometimes causes (generally, fixable) conflicts in default applications, although I'm not familiar with this one.

Edit: Here, try this. Run each of these commands in a terminal and let us know what happens.

```
xdg-open ~
```

```
exo-open ~
```

```
gvfs-open ~
```

```
gnome-open ~
```

---

### Post by UltraZone on 2011-09-17
Hm, alright, I think we are getting closer and closer to solving this problem.

I tried xdg-open ~ : it said no application is registered as handling that.

I tried exo-open ~ : application not installed.  I installed it afterwards.

I tried gvfs-open ~ : same, application not installed.  Installed it afterwards.

I tried gnome-open ~ : same as first one.

Ok, after installing exo-utils and gvfs-bin, executing the four commands above opens Nautilus.  I selected Nautilus when I ran exo-utils.

AND! Places > Home, Desktop, Docs, etc all open now! Woot!

BUT! When I open them I get the busy mouse spinning wheel (I don't know what you call it) for about 10 seconds.  Is there a way to fix that?

Also Shortcuts on GLX Dock work properly now also, so whew! and a BIG THANK YOU.

Copper Bezel, thanks again.  But do you reckon what could have gone wrong?  I mean I'm curious as to the root cause of this problem.

Also, I don't have KDE or XFCE installed, but just the Unity shell, and the good ol Gnome 2.32.

---

### Post by Copper Bezel on 2011-09-17
I don't honestly know what might have caused the problem. I have exo-utils installed myself, because I use Thunar; it's the XFCE equivalent to gnome-open. 

xdg-open is the script that selects which of the binary open commands is appropriate for the current desktop environment. Normally, it would pass up to gnome-open, which is why you got the same result from both of those commands. gvfs-open replaces gnome-open completely in 11.10, but it's not included in the default 11.04 (I don't have gvfs-bin installed myself, though I remember it being there under 10.10) so I don't honestly know what's going on there, but I'm going to guess that gvfs-open is the package that fixed it. You probably don't need exo-utils at all.

I don't really know about the working-in-background cursor, either. Odd.

Anything that opens a location - the Places menus in the Gnome Panel and most docks, "show in folder" in browsers and archive managers, etc. - usually passes to xdg-open and on to gnome-open.

I'm glad that worked, though - installing exo-utils under 11.04 normally *breaks* the Places menu. = ) (But this can be fixed by running exo-preferred-applications, where Firefox or something weird is set as the default file manager.)

Edit: Of course, we still need to fix the problem of whatever is "working" in the background after you open a location, but I'm out of guesses on that.

---

### Post by UltraZone on 2011-09-17
Hm, Ok I see.

I'll mark this thread as effectively solved.

---

### Post by ChrisOfBristol on 2012-05-24
> **garvinrick4 said:**
> Just in case if you right click on Documents or Downloads a directory to be opened by nautilus and then
chose open with and choose file manager and check the box to always open with does it all now open in Nautilus?
I've struggled with this apparently complicated problem for ages, and this simple solution fixes it - thanks! 

(I'm on Mint 13 MATE, but I see no reason why it shouldn't work on Ubuntu.)

---

