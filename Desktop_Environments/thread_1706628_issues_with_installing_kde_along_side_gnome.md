---
title: "issues with installing kde along side gnome"
date: 2011-03-14
forum: Desktop Environments
---

### Post by shoosy on 2011-03-14
Ok i have installed Ubuntu 10.10 and played around a bit and have got it booting into cli instead of the login screen. gnome is my default desktop environment but i wish to run kde along side to play around with.

When i boot into kde using *startx kde (usualy just using startx)* all i get is a mouse, black background and a terminal screen.

Any clue on how to fix this? Im lost.

---

### Post by shoosy on 2011-03-15
well after a bit of stuffing around and looking on the net for help i finally have kde running to a degree of functionality. In the terminal i tipped *xterm *and then it opened a new terminal window i then tipped *startkde *this started up the kde desktop but now i got the issue the terminal is constantly running and it can recognize my dual monitors 

help would be greatly appreciated

---

### Post by Krytarik on 2011-03-15
Wow, this is cool, you got KDE running through a xterm window, which itself was launched from another xterm window! ;-)

Explanation: It seems like you are getting logged into an "xterm" session (!) currently *instead* of Gnome or KDE, for example.

Solution: Do you have to click at your name and enter your password at login, or do you have autologin enabled. If the latter one is the case, you get automatically logged into the last chosen session, but when you log out of your then automatically started session, you should be able to choose the desired "Session" option at the bottom after clicking at your name. The latter should of course also be true for non-autologin. To log out of a "xterm" session, simply enter "exit" into the terminal.

Greetings.

---

### Post by ankspo71 on 2011-03-16
> **shoosy said:**
> "...have got it booting into cli instead of the login screen."

That is what you intended it to do because you wanted a text-only startup, right?

Have you tried the command 'startkde' (or 'sudo startkde') in the console? startkde is the KDE startup script located at /usr/bin/startkde. 
Edited: I just tried  startkde for myself after killing my KDE session, but it needs a running X server to run in. The startkde command takes no options either.

You can also use 'sudo kdm' as needed (or 'sudo gdm' if you prefer) to manually launch the display manager to choose your KDE or Gnome session in the session menu. This might help load the rest of the KDE desktop when you log into KDE. Auto-logins need to be disabled for this to work conveniently for you though.

Hope this helps.

---

### Post by Krytarik on 2011-03-16
Ah, I didn't take your disabled display manager into accout after reading your second post, sorry!

Then follow *ankspo71's* guidance!

---

### Post by Krytarik on 2011-03-16
@ankspo71: Do you know how to specify the default session option when running just "startx"? It seems the OP's has been changed to xterm from what I believe was Gnome before.

---

### Post by ankspo71 on 2011-03-16
Hi Krytarik,
Actually, no I don't. I thought I could see what I could figure out by experimenting for myself but I ended up with the same result as Shoosy did when I tried running startx with different commands. The result was having a running xterm window on my desktop. I didn't even need to use the command 'xterm' to have an xterm window on my desktop. startx followed by any command was enough to cause that problem.

startx always starts the default session (desktop) automatically so I think trick would be to find an easy way to change the default session in the console before using startx. Using the following command to configure the x-session-manager alternatives should help, but it's alot of typing in the console only to start a different session (desktop):
```
sudo update-alternatives --config x-session-manager
```
Then use startx to launch the desktop we just configured as the default.  I only have one desktop environment installed at the moment so I am unable to see how well it works.

It seems to me that it would be easier for me to login graphically with GDM or KDM automatically, or by using 'sudo gdm' or 'sudo kdm'. Using either of these would configure our default desktop automatically once logged in to the desktop so the above command wouldn't be necessary.

I personally like having a graphical startup, and if I ever need to use the console after logging into a desktop, I just use press Ctrl+Alt+F2  to enter the console. I would log out first if I needed my session to be saved though. Ctrl+Alt+F7 is the keys used to bring us back to the desktop, or login screen.

---

### Post by Krytarik on 2011-03-16
> **ankspo71 said:**
> I didn't even need to use the command 'xterm' to have an xterm window on my desktop.
If I understood it right, the OP also got the xterm window, and then launched another one, that's why I was somewhat amused!
> **ankspo71 said:**
> 
startx always starts the default session (desktop) automatically so I think trick would be to find an easy way to change the default session in the console before using startx. Using the following command to configure the x-session-manager alternatives should help, but it's alot of typing in the console only to start a different session (desktop):
```
sudo update-alternatives --config x-session-manager
```
If that is correct, then "~/.dmrc" is getting pulled, I wasn't sure about this, because it is set up by/for the display manager.
> **ankspo71 said:**
> 
It seems to me that it would be easier for me to login graphically with GDM or KDM automatically, or by using 'sudo gdm' or 'sudo kdm'. Using either of these would configure our default desktop automatically once logged in to the desktop so the above command wouldn't be necessary.

I personally like having a graphical startup, and if I ever need to use the console after logging into a desktop, I just use press Ctrl+Alt+F2  to enter the console. I would log out first if I needed my session to be saved though. Ctrl+Alt+F7 is the keys used to bring us back to the desktop, or login screen.The same is true for me. Also, we experienced in another thread, that the system doesn't even boot up faster without GDM. So the advantage of this is marginal. However, the "Exec" command in "/usr/share/xsessions/gnome.desktop" is "gnome-session", for example. I don't know which is stated for KDE, since I don't have it installed. I read somewhere that they use those commands to start the desired session, may be worth a try.

Regarding the keyboard shortcuts, I believe to remember that I had to use Ctrl+Alt+F8 at my mom's machine (with an ATI card) to get back to the desktop, but I'm not sure. May that be?

---

### Post by ankspo71 on 2011-03-16
Hi Again,
I'm using Kubuntu so I can see that the Exec line in "/usr/share/xsessions/kde-plasma.desktop" is Exec=/usr/bin/startkde 

Yeah, it can be Ctrl+Alt+F8 to return to the desktop too, but it all depends on the distribution or maybe even the distribution's version. I can return to my Kubuntu 10.10 desktop with Ctrl+Alt+F7.

---

### Post by Krytarik on 2011-03-16
> **ankspo71 said:**
> Hi Again,
I'm using Kubuntu so I can see that the Exec line in "/usr/share/xsessions/kde-plasma.desktop" is Exec=/usr/bin/startkde 
Ah, like you said earlier. Now, I saw your edit. Then it will not work for the OP, right?
> **ankspo71 said:**
> Yeah, it can be Ctrl+Alt+F8 to return to the desktop too, but it all depends on the distribution or maybe even the distribution's version. I can return to my Kubuntu 10.10 desktop with Ctrl+Alt+F7.
My mom and I both run Ubuntu 10.04. For me it's also Ctrl+Alt+F7 (Nvidia card). Anyway, like I said, I would have to re-check that.

---

### Post by shoosy on 2011-03-16
thanks for the help so far guys i'm slowly getting there, i didn't realize i was in the xterm when i tipping xterm in not the best when mucking around with linux os's we all have to learn somewhere 

i choose to boot into cli by choice not for speed or anything its just because i prefer it over a graphical login 

@ankspo71: did you want me to try those commands in the xterm window or the cli i boot into at the start tipping *sudo startkde *gave me more features one of which i didn't realize till a little earlier that sound wasn't working but didn't fix the dual monitor issue i also never use the auto log on to prevent my brother using my comp. also the *sudo gdm *command I'm trying to avoid using just to be a pain but if needed i will use it unless an alternative can be found

anything to do with the kde-plasma.desktop file wont help me unless i install it

---

### Post by shoosy on 2011-03-16
OK i worked out the dual monitor issue it didn't exist that was user error but audio is still an issue iv got nothing, i have also discovered that straight from the cli i boot into its quicker to type *startx startkde *

---

### Post by ankspo71 on 2011-03-16
> **shoosy said:**
> 

@ankspo71: did you want me to try those commands in the xterm window or the cli i boot into at the start tipping *sudo startkde *gave me more features one of which i didn't realize till a little earlier that sound wasn't working but didn't fix the dual monitor issue i also never use the auto log on to prevent my brother using my comp. also the *sudo gdm *command I'm trying to avoid using just to be a pain but if needed i will use it unless an alternative can be found

Which command? 
the 'sudo update-alternatives --config x-session-manager' command? 
yeah, go ahead and type that into the console (the cli at login) to set your preferred desktop. You'll need to use that command every time you want to switch desktops in the console though... but I suppose you could make a script called "change-desktop" and place it in your /usr/bin/ directory to make the command a little easier. I think it would have to be set as executable too.
```
#!/bin/sh
sudo update-alternatives --config x-session-manager
```
So after creating that script, then placing it in /usr/bin/, you should be able to configure your desktop (then use it) by typing the following command in the console:
```
change-desktop
startx

```


I also tried 'startx startkde' but it gave me a running xterm window on my desktop.

---

### Post by Krytarik on 2011-03-16
Also, don't run KDE as root, please see my earlier post regarding it (that's also the reason why you don't have sound then):
[http://ubuntuforums.org/showthread.php?p=10514878](http://ubuntuforums.org/showthread.php?p=10514878)

---

### Post by shoosy on 2011-03-17
@Krytarik: well that is extremely odd i only have sound when i log into root by tipping *sudo startkde *but when i dont log into root i have no sound :S
i also figured that it was a security risk and wasn't happy with the idea but got it my sound working making me slightly happier about running in root

@ankspo71: i like the idea of writhing a script that shall change my default desktop manager, the only problem is i have no clue where to start on doing so as i said earlier i'm new to modifying Linux not to much to using Linux 

if either of you were able to give me a hand with that i would be greatly appreciated 

thanks for your help so far I'm running kde desktop and accessing it via gdm but id still prefer to be able to boot it form the terminal. with your help iv gone from taking baby steps to leaps and bounds

---

### Post by Krytarik on 2011-03-17
> **shoosy said:**
> @Krytarik: well that is extremely odd i only have sound when i log into root by tipping *sudo startkde *but when i dont log into root i have no sound :S

Ok, I thought meant that you *don't* have sound when running startkde as root.

Now, that you logged into KDE through GDM, you should be able to run "startx" to get to KDE. Please try it, if not already done. Also, do you have sound when starting KDE through GDM?

We will take care of the script later, if you got "startx" working, otherwise it makes no sense.

EDIT: Another thing, please check what result the command "gnome-session" yields.

---

### Post by shoosy on 2011-03-17
i get the sound when running through gdm i shall try now

---

### Post by shoosy on 2011-03-17
ok no it dose not set kde as my default environment still boots gnome by typing *startx* but kde after booting from gdm has full functionality it also has full functionality after changing *sudo update-alternatives --config x-session-manager' command *thats why in thinking 
make the script

---

### Post by Krytarik on 2011-03-17
When you run the command *"sudo update-alternatives --config x-session-manager"*, select KDE there, and then run *"startx"*, you are still getting into Gnome? Because that's what the those command should affect.

Also, did you try the command *"gnome-session"* I mentioned (in my edit)?

---

### Post by Krytarik on 2011-03-17
I googled a bit since I wasn't really clear about how to specify the default desktop environment (Gnome or KDE in your case) when running *"startx"*, and what the effect of the command *ankspo71* gave us should be. I found two sites regarding the file "~/.xinitrc" (in your home directory), the first I did already know, but since I am using GDM, you may just try it:
[http://www.tuxfiles.org/linuxhelp/changeman.html](http://www.tuxfiles.org/linuxhelp/changeman.html)
[http://ubuntuforums.org/showthread.php?t=1645209](http://ubuntuforums.org/showthread.php?t=1645209)

---

### Post by shoosy on 2011-03-17
the command *sudo update-alternatives --config x-session-manager *does change it from gnome to kde yes it works changing the desktop enviroment from gnome to kde followed by *startx* then kde boots fine no issues  i haven't tried your command want me to put it in xterm or just normal terminal cli boot one?

---

### Post by Krytarik on 2011-03-17
No need to try it anymore, since you can apparently choose between KDE an Gnome by using the *"alternatives"* command, and because *"startkde"* also doesn't work any good.

But try using the mentioned "~/.xinitrc" for *"startx"*, that would be of interest now.

---

### Post by ankspo71 on 2011-03-17
Okay, I think we have this figured out now :D 
I forgot all about the xinitrc file.

Choose KDE and start it: (tested and works)
```
echo "exec startkde" > ~/.xinitrc
startx
```

Choose Openbox and start it: (tested and works)
```
echo "exec openbox-session" > ~/.xinitrc
startx
```

And I am assuming Gnome is this: 
```
echo "exec gnome-session" > ~/.xinitrc
startx
```

---

### Post by shoosy on 2011-03-17
ok the 2 commands 

echo "exec startkde" > ~/.xinitrc
startxand 
echo "exec gnome-session" > ~/.xinitrc
startx
they change the desktop environment and so on but then with both of them i have no audio on both using this 
also discovered that when i bot into kde i have no shutdown/reboot  commands unless i make it default desktop environment or go threw gdm

---

### Post by Krytarik on 2011-03-17
Then please try the command posted in the thread I mentioned earlier, the corresponding commands for you would be like this:
```
echo "exec ck-launch-session dbus-launch --exit-with-session startkde" > ~/.xinitrc
startx
``````
echo "exec ck-launch-session dbus-launch --exit-with-session gnome-session" > ~/.xinitrc
startx
```

---

### Post by shoosy on 2011-03-18
ok after trying the last commands the xserver crashes and the *startx *command no longer works

---

### Post by Krytarik on 2011-03-18
> **shoosy said:**
> ok after trying the last commands the xserver crashes and the startx command no longer works
Ok, I tested the commands by myself now, and there is apparently a typo in those, correct is "--exit-with-session", instead of "-exit-with-session". The strange thing is, that I saw those (general) commands in two different posts, the one I posted here, and another one, this time without the full paths but with another (apparently invalid) option. And both references had the same typo in the command.

Anyhow, I corrected the commands in the previous post. I tested it with XFCE and Gnome, both work, both have sound. Please try it again now.

---

### Post by shoosy on 2011-03-18
ok with the new command everything seems to function well sound and i can shut down and restart now to thanks for your help so far its greatly apreciated 

i seem to have an issue logging of kde into cli though but is functions perfect with the command tho but it never seems to save my resolution at 1920x1080 on my 1st monitor know how to fix this?

---

### Post by shoosy on 2011-03-18
ok logging off into cli is no longer an issue :)

---

### Post by Krytarik on 2011-03-18
> **shoosy said:**
> it never seems to save my resolution at 1920x1080 on my 1st monitor know how to fix this?
I'm afraid you need to setup a "xorg.conf" to fix this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Is your chosen resolution remembered when you launch KDE via the "alternatives" way or GDM?

Now that the startx way works, you can create scripts for those commands, those instructions apply to each set of commands:
- create a text file in "/usr/local/bin", choose a name of your liking, but NOT "startkde" or "gnome-session"
- paste the commands into it, save it
- make the script executable
```
sudo chmod +x /usr/local/bin/SCRIPTNAME
```Now you can launch the desired sessions by simply entering the respective chosen names.

---

### Post by shoosy on 2011-03-18
the screen res wont save no matter what il try that link

---

### Post by shoosy on 2011-03-19
ok everything is done from the cli all i type is *startkde-session* to start kde and *startgnome-session *for gnome everything but the screen res at the moment which I'm working on right now thanks for your help its been greatly appreciated now one last thing to do ic change the post to solved

---

### Post by Krytarik on 2011-03-19
> **shoosy said:**
> ok everything is done from the cli all i type is *startkde-session* to start kde and *startgnome-session *for gnome 
Names like "kde" and "gnome" would also be sufficient, fewer to type. ;-)
> **shoosy said:**
> 
everything but the screen res at the moment which I'm working on right now thanks for your help its been greatly appreciated now one last thing to do ic change the post to solved
If you need help regarding those, please start a new thread and send me a private message about it.

---

