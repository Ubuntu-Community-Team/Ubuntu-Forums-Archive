---
title: "KDE Cursor Them has taken over! How do I Restore Human Cursor Theme?"
date: 2007-10-20
forum: Desktop Environments
---

### Post by LordKelvan on 2007-10-20
Hi:

This is a bit of a long story.  I switched to Linux back in 7.04 (Feisty Fawn), and one day decided to try out Kubuntu alongside my Ubuntu install.  Eventually I switched back, but kept on using Amarok on Ubuntu.  I noticed this weird problem where my cursor changed whenever I clicked on anything in Amarok (this happened even when I clicked on the Amarok task tray icon).  Instead of the normal Human cursor, I got this black cursor (like the old-school Microsoft ones).  Since this only happened with Amarok, I figured it was just a result of running a KDE app in Gnome, and lived with it.

Just a few days ago, I upgraded to 7.10 (Gutsy Gibbon) and now that black cursor thing is permanently in use, and not just when I click on things in Amarok.  Basically, my normal cursor has been replaced by a black cursor, the "busy" cursor is no longer a spinning circle but this weird square black watch, and my regular hand cursor (when I click on links) has been replaced by this weird hand cursor (again like in the old Microsoft OS's)

I checked In System>Preferences>Appearance, and I have indeed selected the default cursor theme.  Can someone please help me?  I have searched around the forums, and the closest I can find was in this thread: [http://ubuntuforums.org/showthread.php?t=564335&highlight=kde+cursor+theme+in+gnome]("http://ubuntuforums.org/showthread.php?t=564335&highlight=kde+cursor+theme+in+gnome")

This is driving me crazy !! 

Thanks in advance, 
LK

---

### Post by kaikai581 on 2007-10-21
Hi LordKelvan,

I found the solution by accident. I think you can give it a try. At least it works for me.

[http://ubuntuforums.org/showthread.php?t=238902&highlight=firefox+cursor](http://ubuntuforums.org/showthread.php?t=238902&highlight=firefox+cursor)

---

### Post by LordKelvan on 2008-01-21
Hi:

kaikai581: Thanks for your help, but that post didn't fix it for me.

At school I have a fresh install of Ubuntu 7.10, and I basically compared the settings on the school computer with my home computer.  I ended up changing my cursor theme to be "DMZ-White" (that was apparently the one I had in 7.04), instead of "Default".  Its now more or less what I had back in 7.04.  Except there are still a few issues that I cannot solve:

1) In jEdit (its a great Java-based text editor) I still get that old ugly cursor - its like some applications are ignoring my mouse cursor theme.  How do I get these applications to behave properly?

2) When I log in, for like maybe 5-10 seconds the old ugly cursor appears.  So the sequence of events is:
normal cursor (pre-logging in) ---> ugly old cursor (after logging in, for about 5-10 seconds) --> normal cursor (rest of the time).

3) When I look at the list of different mouse cursors in the Appearance dialog box, I notice that there is no icon beside the "Default" cursor (its blank), whereas there are icons beside the rest.

I know my second and third problem are pretty minor, but I think they are part of the reason I am having the first problem.  I think the second problem shows some program is trying to override my mouse cursor theme, and the third problem suggests that my "Default" mouse cursor theme is not properly pointing to anything, which may cause issues if an app blindly picks the "Default" mouse cursor theme.  If anyone has any ideas on how to fix any of these problems, that would help.

My setup:

Ubuntu 7.10 (using Gnome)
Compiz enabled

Cheers,
LK

---

### Post by LordKelvan on 2008-01-23
Hi:

I believe I have finally figured out the problem.  

**Problem #3**
There is a "default" cursor, which merely links to one of the available cursor themes on your system.  Ubuntu looks inside /usr/share/icons/default for a softlink called index.theme.  On most systems, index.theme points to /etc/alternatives/x-cursor-theme, which in turn points to /usr/share/icons/DMZ-White/cursor.theme (unless of course you've changed any of this).

On my system, I had a index.theme which was located at ~/.icons/default and pointed to /usr/share/icons/Human/index.theme.  This was causing problems for 2 reasons:

[LIST=1]
/usr/share/icons/Human/index.theme is not a valid cursor theme file (I think its for the Human Gtk/Metacity theme)
[*]The incorrect index.theme softlink I had in ~/.icons/default was overriding the correct index.theme in /usr/share/icons/default
[/LIST]

So I just deleted ~/.icons/default/index.theme, and now in the Gnome Appearances dialog box, the "Default Pointer" entry correctly shows the DMZ-White cursor icon.  

**Problem #1**
I had previously used the CompizConfig Settings Manager (CCSM) to set the cursor theme (its under General Settings) to be DMZ-White, and had chosen DMZ-White under Cursors in the Gnome Appearances dialog box.  I have now changed both settings back to "default", since "default" now correctly points to DMZ-White.

**Problem #2**
I believe that previously my various settings were battling it out (the incorrect ~/.icons/default/index.theme, the CCSM cursor theme setting and the Gnome Appearance cursor theme setting).  This was causing that brief glitch right after I logged in where the ugly cursor was being used.


Hope this helps anyone else facing a similar problem.

Cheers,
LK

---

