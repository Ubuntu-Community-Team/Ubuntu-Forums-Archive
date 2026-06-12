---
title: "How to remove GNOME3"
date: 2015-11-02
forum: Desktop Environments
---

### Post by Elijah_Duffy on 2015-11-02
A few days ago I installed GNOME3 by typing: ```
sudo apt-get install ubuntu-gnome-desktop
``` in the TTY1 terminal.
I then typed: sudo dpkg-reconfigure gdm
And restarted my computer.

Within five minutes of using GNOME, I really do not like it. So my question is how do I remove GNOME? I have been able to switch back to lightdm (so I'm back to the normal Ubuntu login screen, but still have the GNOME boot, etc...) and if my memory is correct, I also tried to remove the main gnome-shell. I also tried to remove gdm, gnome, tried using sudo apt-get purge gnome-shell. If needed, don't worry about what I removed, just let me know how to remove it as if it was all there. And if I have to I will reinstall the removed packages, or remove them from the uninstall list (if that is the case to remove GNOME)

Any help to remove GNOME3 would be greatly appreciated.
If I need to clarify anything, please let me know.

Thanks again!

---

### Post by Bucky Ball on 2015-11-02
Welcome. Boot to a different environment (choose one from the Sessions menu at login screen or boot to the CLI or recovery mode and drop to a root shell), then:

```
sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get autoremove
```

Log out and log back in?

There is a ton of info regarding this [here]("https://duckduckgo.com/?q=remove+gnome+desktop"). Let us know if you get stuck. :)

---

### Post by grahammechanical on 2015-11-03
Be careful when you talk about removing Gnome 3. It is still the desktop environment that Unity sits on. The fact is that ubuntu-gnome-desktop is just a meta package that is used to pull in lots of Gnome utilities that are used in Ubuntu Gnome. I do not think that removing ubuntu-gnome-desktop meta package will remove those utilities.

And you are not the only one.

[http://ubuntuforums.org/showthread.php?t=2301264](http://ubuntuforums.org/showthread.php?t=2301264)

Regards.

---

### Post by kurt18947 on 2015-11-03
Before removing gnome3 desktop, have you looked at extensions.gnome.org? I use Ubuntu-Gnome as my 'daily driver'. I don't find 'out-of-the-box' gnome usable. A handful of extensions and gnome-tweak-tool make gnome3 quite usable for me.

---

### Post by Elijah_Duffy on 2015-11-07
That's true, but only if you have a good computer. Since some of the RAM for my computer was defective, I am left with only 2GB and haven't had a chance to get more yet. I am not interested in simple tweaking GNOME, but I would like it fully removed no matter what. I have removed the gdm, and am back with the normal Ubuntu log in screen, but a lot of software installed with sudo apt-get ubuntu-gnome-desktop is still there along with the weird GNOME boot screen/animation.

---

### Post by Elijah_Duffy on 2015-11-08
> **Bucky Ball said:**
> Welcome. Boot to a different environment (choose one from the Sessions menu at login screen or boot to the CLI or recovery mode and drop to a root shell), then:

```
sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get autoremove
```

Log out and log back in?

There is a ton of info regarding this [here]("https://duckduckgo.com/?q=remove+gnome+desktop"). Let us know if you get stuck. :)

Thanks. I tried that and it did not work. Do you have any other ideas? I ended up simply typing **sudo apt-get remove gnome-*** which removed everything GNOME related, and the Ubuntu Desktop. So then I just reinstalled Ubuntu desktop. I am going to try removing GNOME on a different computer without removing Ubuntu Desktop so any other ideas are still appreciated.  

I will make another reply explaining how I removed it.

---

### Post by Elijah_Duffy on 2015-11-08
In case anyone else has this problem and sees my post, I will explain how I removed GNOME 3 from Ubuntu 15.10

First I switched to **tty1** by pressing **Ctrl+Alt+F1**, then in the terminal windows that appears, logging in by typing your **username**, pressing **enter**. Then typing your **password**, and pressing **enter** once again.  

I then typed **sudo apt-get remove gnome-*** which removes all software with **gnome** in it's name or description. (If that is not what typing **... remove gnome-*** does, please feel free to correct me as I am not 100% sure myself) Please note, that when your computer is up and running on the default Ubuntu Desktop, you may have to reinstall some application downloaded  from the Ubuntu Software Center as some of them are related to gnome and  may be removed when **sudo apt-get remove gnome-*** is run.

Then I rebooted my computer by typing **sudo reboot** or **sudo shutdown -r now** if the first doesn't work. (Which it doesn't appear to when logged in on the **tty** terminal windows as root)

For me, my computer then sits around taking forever to turn on (it doesn't turn on at all and just sits on the Ubuntu boot screen saying it's loading unless you have a actual desktop such as **ubuntu-desktop**, or **ubuntu-gnome-desktop**). So I turned my computer off my simply pressing the power button until it turned off. Then turn on your computer and when the GNU boot options come up, select **Advanced Ubuntu Options** with your up/down arrows, press **enter**, and in the next menu select the Linux that has **(recovery)** at the end of it's name.
Re: How to remove GNOME3
Once the computer turns on in recovery mode, select auto remove unneeded packages and follow the command steps, but when it asks to remove packages, just say no and press **escape** to return to the recovery menu. The reason for doing this is to easily unlock an encrypted hard drive such as mine.

In the recovery menu select **enable networking**. If needed press **escape** once networking is enabled. 

Once back at the recovery menu again, select **drop to root terminal**. This will take you to a root terminal. You can always return to the recovery menu by pressing **escape**. **WARNING: IN THE ROOT TERMINAL, YOU HAVE FULL ACCESS TO ALL HIDDEN OF PERMISSION LOCKED COMPUTER FILES, AND COULD EASILY DELETE NEEDED SYSTEM FILES IF YOU ARE NOT CAREFUL. NOT EVEN SUDO IS NEEDED TO RUN ROOT COMMANDS.** Then type **apt-get ubuntu-desktop** which will download and install the normal Ubuntu desktop and all built-in apps that may have been removed.

All that's left to do is restart your computer and your computer should be back to normal. I will update this post later after I have checked that the names of the menus in recovery mode were correct.

---

