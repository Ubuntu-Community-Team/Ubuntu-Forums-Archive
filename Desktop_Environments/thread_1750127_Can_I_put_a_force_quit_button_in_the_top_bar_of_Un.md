---
title: "Can I put a force quit button in the top bar of Unity in 11.04"
date: 2011-05-05
forum: Desktop Environments
---

### Post by jesse.au on 2011-05-05
I would like to put a button to force quit non responsive applications on the top bar in Ubuntu 11.04. This was one of the most helpful functions in previous versions of Ubuntu. Is there a way to regain this functionality so that I do not have to go to manually kill the process using command line or system processes.

---

### Post by warroomcbw on 2011-05-06
> **jesse.au said:**
> I would like to put a button to force quit non responsive applications on the top bar in Ubuntu 11.04. This was one of the most helpful functions in previous versions of Ubuntu. Is there a way to regain this functionality so that I do not have to go to manually kill the process using command line or system processes.

I ditto that!

---

### Post by retbak on 2011-05-06
this would be good

---

### Post by mc4man on 2011-05-06
You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

For a standalone launcher icon
create .desktop
```
gedit ~/.local/share/applications/quit.desktop

```
C&P this in, adjust Icon= line to icon of choice
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```
Save, then open home folder (view > show hidden files), browse to 
.local/share/applications
And drag the quit.desktop onto the launcher
If need be log out/in to set

To use - click on launcher X appears, put on window, left click.

To add to a group using quicklists - see here, part of a utility group icon
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

_To add to power button_ - several ways, do only 1, my preferred is the last method (/usr/local/.. and link

create the desktop as before, then either make a link to it in or just move it to
/usr/share/indicators/session/applications 

Or just create the .desktop in there
```
gksudo gedit /usr/share/indicators/session/applications/quit.desktop
```

Or create in /usr/local and then link
```
mkdir -p  /usr/local/share/applications && \
gksudo gedit /usr/local/share/applications/quit.desktop


```
Then create the link
```
sudo ln -s /usr/local/share/applications/quit.desktop /usr/share/indicators/session/applications/quit.desktop

```

For multiple users quit.desktop must either be in /usr/share/indicators/session/applications or in /usr/local/share/applications/ and linked

---

### Post by redbikemaster on 2011-05-06
I'm doing this too. That is cool how that works!
Thanks mc4man!

---

### Post by robgraves on 2011-05-08
> **mc4man said:**
> You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

For a standalone launcher icon
create .desktop
```
gedit ~/.local/share/applications/quit.desktop

```C&P this in, adjust Icon= line to icon of choice
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```Save, then open home folder (view > show hidden files), browse to 
.local/share/applications
And drag the quit.desktop onto the launcher
If need be log out/in to set

To use - click on launcher X appears, put on window, left click.

To add to a group using quicklists - see here, part of a utility group icon
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

To add to power button - several ways
create the desktop as before, then either make a link to it in or just move it to
/usr/share/indicators/session/applications

Or just create the .desktop in there

that is awesome, thank you, worked like a charm, i had been missing my force quit icon.

---

### Post by Copper Bezel on 2011-05-08
I just use a Compiz keybinding for xkill (Super+X in my case). It's a little less obtrusive (because an icon on the panel to kill nonresponsive programs seems like admitting defeat.)

---

### Post by mc4man on 2011-05-08
> **Copper Bezel said:**
> I just use a Compiz keybinding for xkill (Super+X in my case). It's a little less obtrusive (because an icon on the panel to kill nonresponsive programs seems like admitting defeat.)

That sounds good, (and easier), my second choice would be the power button

Seem like it's about time for me  to do some learning about compiz now that ubuntu is embracing it a bit more than in the past.

---

### Post by jesse.au on 2011-05-08
> **mc4man said:**
> You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

For a standalone launcher icon
create .desktop
```
gedit ~/.local/share/applications/quit.desktop

```
C&P this in, adjust Icon= line to icon of choice
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```
Save, then open home folder (view > show hidden files), browse to 
.local/share/applications
And drag the quit.desktop onto the launcher
If need be log out/in to set

To use - click on launcher X appears, put on window, left click.

To add to a group using quicklists - see here, part of a utility group icon
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

To add to power button - several ways
create the desktop as before, then either make a link to it in or just move it to
/usr/share/indicators/session/applications

Or just create the .desktop in there

Thanks! That is AWESOME. thanks for that

---

### Post by Wheel on 2011-05-09
Thanks, mc4man.
Force Quit was one of the little extras I was wanting.
It now sits on my Power Button drop-down.
Sweet.

---

### Post by pitchizig on 2011-05-09
Thank you Mc4man, Force Quit added to Power Button. Works fine.

---

### Post by Erik500002 on 2011-05-11
Indeed Thanks mc4man just what I was looking for takes a while to get used to the new unity interface, but overall looks awesome.

---

### Post by edfast on 2011-05-19
> Or create in /usr/local and then link
```
mkdir -p  /usr/local/share/applications && \
gksudo gedit /usr/local/share/applications/quit.desktop
 

```
Then create the link
```
sudo ln -s /usr/local/share/applications/quit.desktop /usr/share/indicators/session/applications/quit.desktop

```
 
For multiple users quit.desktop must either be in /usr/share/indicators/session/applications or in /usr/local/share/applications/ and linked
 
Hrm,
 
terminal (in another language) returns:
 
command 'gksudo' not available in 'usr/bin/gksudo'
gksudo: command not found
 
anyone experience this?

---

### Post by rtimai on 2011-05-20
Very interesting thread. Has anyone actually encountered an instance when you HAD to use force-quit -- and it worked? It will work when you DON'T HAVE TO use it... but when you had an actual application freeze up on you?

I'm wondering, because I used to use the force-quit applet in Maverick, but in Unity, whenever an application froze, the entire desktop also locked up and nothing responded to mouse-clicks (and so, the panel or launcher would be non-responsive as well.) 

What I had to do was Ctrl-Alt-F1 to the TTY1 console and run "sudo shutdown -P now"

Later on, I found that I could re-enable Ctrl-Alt-Bkspace (kill/restart Xorg) in Keyboard Options.

ASIDE (only partly related): What's weird is every time I restart X or login/out, I find the desktop on a different console, usually tty8 or 9, depending on how many times X is restarted. I've seen this mentioned elsewhere, and the general consensus was it must be by-design, but not known why. So, to have your desktop located in the "expected" console tty7, you'd have to restart the operating system, not just the graphical system. This might be important to those writing shell scripts...

---

### Post by Copper Bezel on 2011-05-20
The unpredictable location for the display started in 10.10, not 11.04 - or at least, I first noticed it on 10.10 while using CompizStandalone. It's associated with a handful of other differences that Krytarik (who uses the LTS) and I have noticed lately - for instance, loading a windowed application from another user, such as to edit gconf settings for gdm, requires passing along the display variable, or it won't launch. It comes with the perk of making it much easier to create custom sessions (like CompizStandalone) without dealing with xinit. 

I'm still on 10.10, and I make frequent use of xkill for nonresponsive apps. If the window manager hangs (as you're describing) that's a separate problem. If nonresponsive apps hang Compiz in 11.04, then that's another reason for me not to upgrade, but you really ought to file a bug report on that. If you can, determine whether it's related to the Unity plugin or whether it happens under Compiz regardless.

edfast, although it's the graphical equivalent of sudo, the command is gksu.

---

### Post by NerdWermz on 2011-05-20
> **mc4man said:**
> You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

For a standalone launcher icon
create .desktop
```
gedit ~/.local/share/applications/quit.desktop

```C&P this in, adjust Icon= line to icon of choice
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```Save, then open home folder (view > show hidden files), browse to 
.local/share/applications
And drag the quit.desktop onto the launcher
If need be log out/in to set

To use - click on launcher X appears, put on window, left click.

To add to a group using quicklists - see here, part of a utility group icon
[http://ubuntuforums.org/showthread.php?p=10778758#post10778758](http://ubuntuforums.org/showthread.php?p=10778758#post10778758)

_To add to power button_ - several ways, do only 1, my preferred is the last method (/usr/local/.. and link

create the desktop as before, then either make a link to it in or just move it to
/usr/share/indicators/session/applications 

Or just create the .desktop in there
```
gksudo gedit /usr/share/indicators/session/applications/quit.desktop
```Or create in /usr/local and then link
```
mkdir -p  /usr/local/share/applications && \
gksudo gedit /usr/local/share/applications/quit.desktop


```Then create the link
```
sudo ln -s /usr/local/share/applications/quit.desktop /usr/share/indicators/session/applications/quit.desktop

```For multiple users quit.desktop must either be in /usr/share/indicators/session/applications or in /usr/local/share/applications/ and linked

I'm new at the coding aspect, so can you please explain how this knows what application is not responding?  Whenever I need to do this I us the ps command from the terminal and use the kill command on the PID.  If there is a one click easy way i would like to know. :P

thanks.

---

### Post by Copper Bezel on 2011-05-20
Well, xkill doesn't actually kill the process itself, just the window, but the severed connection to the xserver generally kills the process, too. It has a [_Wikipedia page_]("http://en.wikipedia.org/wiki/Xkill"). = )

It doesn't have root permission, though, so it can't kill elevated windows, if that ever came up.

---

### Post by rtimai on 2011-05-20
Copper Bezel,

I don't have any more application/Compiz freezes since LibreOffice fixed the crash on loading a document. But thanks for the xkill command reminder, I've been trying to remember what it was, and used "shutdown" because I couldn't find the proper command. I thought I remembered the command was "restart X" or "restart X.org" but I get "unknown job" errors now. 

For the moment, however, re-enabling Ctrl-Alt-Bkspace to restart Xorg seems to be my best solution -- should I ever need to restart the desktop again. 

Yes, I noticed the desktop moving consoles with Maverick (when logging out/in,) and then noticed it again recently when testing Ctrl-Alt-Bkspace. Curious that so few others have mentioned it however. But, as you confirmed it was intentionally designed that way, I guess it's not an issue. Well, except that users should be instructed to try tty8,9,10...

---

### Post by Copper Bezel on 2011-05-21
Yes, certainly something to keep in mind for guides, and as I said, I wasn't entirely certain that the difference wasn't being caused by my using Standalone until you confirmed it with Gnome.

The xkill command doesn't kill the xserver - it's the same command used in the force quit launcher suggested in this thread. I never can remember the kill command to kill x, either, and I keep Ctrl+Alt+Backspace on hand, as well.

---

### Post by coffeecat on 2011-05-21
> **Copper Bezel said:**
> I never can remember the kill command to kill x

You could use the magic key combination of AltGr + SysReq/Print + k. Strictly speaking that kills all processes on the current virtual console, but if X is running in your current console that's an effective way to kill X. X restarts and you get returned to the login screen.

---

### Post by andy123456 on 2011-05-25
Hey guys I am a noob and I don't get the instructions am I supposed to make a .desktop launcher or am I supposed to copy the code in the terminal. I tried to put the code in the terminal but it wouldn't let me save the document. I also tried making a launcher with the name .desktop and the source was the code mc4man talked about but it wouldn't save either. 
Thank you for your patience!!

---

### Post by DanaLou on 2011-05-26
> **mc4man said:**
> You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

For a standalone launcher icon
create .desktop
```
gedit ~/.local/share/applications/quit.desktop

```
C&P this in, adjust Icon= line to icon of choice
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=xkill
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```
Save, then open home folder (view > show hidden files), browse to 
.local/share/applications
And drag the quit.desktop onto the launcher
If need be log out/in to set

To use - click on launcher X appears, put on window, left click.


I just wanted to chime in with another heart-felt THANK YOU for this trick. I don't use UNITY, but this works for the GNOME desktop perfectly; I just dragged to my top bar. 

I love Ubuntu!! :guitar:

Oh, andy123456 ... the first part gets cut & pasted into terminal. Then go into your .local/share/applications directory and find the quit.desktop file; in my case, I dragged that file onto my top bar ... a cool red circle with a white "X" appears. To use it just left-click and you get a skull & cross-bones icon; then click on the app you want to kill. Cool stuff :D

---

### Post by andy123456 on 2011-05-26
Thank you for replying DanaLou! After you told me to put the code into the terminal, it again told me it couldn't save the file. So I wen into the .local/share and there wasn't no application folder so I created a folder called application and then I typed the code into the terminal again and this time it worked! Then after trying to open it it said that it couldn't open it (something about not have permission). So then I right clicked the quit.desktop file and went to permissions and checked the box that said allow executing file as program. Anyways thank you everybody and especially the poster for posting this.

---

### Post by Snosrap68 on 2011-08-09
**p e r f e c t .....thanks**

---

### Post by ccstark on 2011-08-11
mc4man: "You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon."

Tried this as suggested.  Exactly what I wanted.  Thanks mc4man.

---

### Post by jal4568 on 2011-08-21
Thanks mc4man! I'm slowly getting used to Unity and don't hate it but I have been sorely missing my "Force Quit" option. Your solution worked flawlessly!:D

---

### Post by Andavane on 2011-08-30
> **mc4man said:**
> You can add a 'force quit' icon to the launcher or add as part of a group of r. click options on a launcher icon
It can also be added to the power button drop down

F....

For multiple users quit.desktop must either be in /usr/share/indicators/session/applications or in /usr/local/share/applications/ and linked

works a treat.
Extremely impressed!!

---

### Post by rg4w on 2011-08-30
If it's necessary to force-quit apps often enough to warrant a shortcut for it there's a bigger problem at play.....

---

### Post by MARP1961 on 2011-08-30
All this is very interesting; but in earlier classic Gnome 2, a simple right click on a panel was all that was needed to open the 'Add To Panel' option.

It is for little reasons like this I am pinning my hopes on Gnome 3 Shell instead of the totally inflexible Unity.

---

### Post by srabee on 2011-09-13
ORRRRR, you could do it the really easy way. Right click on the upper task bar & click on "Add to Panel". Scroll to "Force Quit" & add. It will automatically appear on your top taskbar. I always forget about this option whenever I upgrade. I just spent 20 minutes trying to find/install it. Then when I remembered about the taskbar menu, it took a whole 30 seconds.... If I want it hidden, maybe I'll try dragging the file I just made reading the previous posts & put it in my launcher. Happy Ubuntu-ing!

Woops! I guess MARP1961 just mentioned that in the post right above me. Didn't see that til now.

---

### Post by coffeecat on 2011-09-14
> **srabee said:**
> ORRRRR, you could do it the really easy way. Right click on the upper task bar & click on "Add to Panel". Scroll to "Force Quit" & add. It will automatically appear on your top taskbar.

@srabee, your suggestion only works in classic gnome, not in Unity which was the OP's question. Since the question has been answered to the OP's satisfaction and since the OP has not logged in for several weeks, I'll close this thread.

Thread closed.

---

