---
title: "Title vanishes at startup, must manually restart window manager"
date: 2009-09-15
forum: Desktop Environments
---

### Post by inspired on 2009-09-15
Hi folks,
This morning my laptop was in standby and lost power. The battery went dead and it obviously shut down in a non-clean way.
I then started the computer up and the system had resorted to some odd configuration settings. For instance the keybindings have have setup in gnome configuration went back to older settings I had many months ago. Also, the window manager does not load correctly... there is no title bar, globalmenu-panel-applet does not work, and when I open an app it will often overlay the top panel. The only way I found to temporarily fix this is to load the Compiz Fuzion Icon taskbar applet, then I use that to RELOAD WINDOW MANAGER.

I don't actually use Compiz. It is installed, but I turned it off a long time ago.

After reloading the window manager, all is good. globalmenu-panel-applet works, apps don't open over the top panel, and the app windows have their title bar restored (along with the controls on that bar).

BUT when I next boot up the system the same thing occurs all over again. Something is broken.

How can I go about fixing this?

With thanks,
Jonathan

---

### Post by gettinoriginal on 2009-09-16
You don't say what window manager you are using, I am assuming metacity, so try using terminal and type:
```
metacity --replace
```
This should reset the default.  :P

---

### Post by inspired on 2009-09-17
> **gettinoriginal said:**
> You don't say what window manager you are using, I am assuming metacity, so try using terminal and type:
```
metacity --replace
```
This should reset the default.  :P
Thanks. Tried that and it made the entire interface non-responsive, and had to then crash out of OS and restart.
Upon restart, the issue is still there.

Use, I use metacity... although it makes no difference. If I activate compiz the same issue is there. Either way, the only way I currently have found to work with this system now is it "Reload Window Manager" from the Compiz Fuzion Icon.

Any further suggestions are greatly appreciated.

Thanks,

Jonathan

---

### Post by etnlIcarus on 2009-09-17
If no other WM is running, you don't need the --replace argument.

If opening a run dialogue and running metacity works okay, you could add an entry to $HOME/.config/autostart/

It's also worth playing around with the gnome session manager. It's quite possible that this is where your problem is originating from.

---

### Post by inspired on 2009-09-24
> **etnlIcarus said:**
> If no other WM is running, you don't need the --replace argument.

If opening a run dialogue and running metacity works okay, you could add an entry to $HOME/.config/autostart/

It's also worth playing around with the gnome session manager. It's quite possible that this is where your problem is originating from.
Thanks. So what I have done is used the autostart thing to sort it out. It would be nice to just fix it rather than use a workaround, but I guess there is no harm done this way.
I am not sure how to play around with the session manager. Any tips?

With thanks,
Jonathan

---

### Post by etnlIcarus on 2009-09-24
> **inspired said:**
> I am not sure how to play around with the session manager. Any tips?

Take up drinking. Gnome's session manager is (or at least used to be) a pain in the ****.

Somewhere in the session manager, should be a list of apps, which includes metacity. You should be able to manipulate that, so that metacity 'restarts upon close/crash'.

It's also probably a good idea to enable the option (where ever it is) to 'save session on logout'. 

If you: 
- enable this behaviour 
- close the session manager
- have open only the stuff you want started automatically at login
- logout
- log back in
- open session manager and disable the 'save session on logout' option

Then, *hopefully*, whenever you log into Gnome, your desktop will restore itself to the state it was in when you logged out during the above process.


Only thing to consider while doing this, is that launchers in your autostart directory can conflict with this custom Gnome session.

I found in Xfce4.6 (similar session manager to Gnome) that conky was playing up because conky was running when I logged out (thus it got saved to the session) and I *also* had an autostart entry for it, which resulted in conky being loaded twice, because the, "session", and, "autostart", scripts function independently of one another.

While playing with the session, it's probably best to disable the autostart entry. Metacity loading twice might cause it to play up.

---

### Post by richardh9936 on 2011-02-24
Had a similar issue today.  Fixed with 
compiz --replace &

---

