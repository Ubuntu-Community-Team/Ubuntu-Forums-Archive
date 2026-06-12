---
title: "how can i permanently force lubuntu to use compiz after restart?"
date: 2013-10-12
forum: Desktop Environments
---

### Post by dawciobiel on 2013-10-12
I installed compiz on my lubuntu 13.04 and how can i permanently force lubuntu to use it - for exmaple after restart?
It work when i will lunch:

```
$ compiz --replace
```

But i dont want to lunch this command every time im logging in. Do i have to type this command to .bashrc or something?

---

### Post by Frogs Hair on 2013-10-12
Have you tried to add compiz to startup applications or the Lubuntu equivalent ?

---

### Post by ajgreeny on 2013-10-12
It is not as easy in Lubuntu as it is in Ubuntu or Xubuntu to add applications to your session autostart list, but here are some possibilities that may help you. I never bother with compiz these days, but I think the first option below is the place to put the command, ie /home/username/.config/lxsession/Lubuntu/autostart.

EDIT:
Yes that is where it needs to go; I just tried it out of curiosity.

**Lubuntu autostart applications.**

Include command to start apps in list in:-
/home/username/.config/lxsession/Lubuntu/autostart
    eg,
    
parcellite            normal command
gmail-notify-delay        shell script copied to /usr/bin
bash -c "sleep 10; conky"    compound command to give 10 second delay

Other items go in either
    /etc/xdg/autostart    as the .desktop configuration file, ie the launcher copied /usr/share/applications
or
    /etc/xdg/lxsession/Lubuntu/autostart    in form
    
@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@notap  (this is a shell script I wrote to stop trackpad tap-to-click which I then copied to/usr/bin)

---

### Post by DuckHook on 2013-10-12
Just a curiosity question...

Why Compiz? Most people who install Lubuntu do so because they *don't* want Compiz. Those who want it tend to install Ubuntu, and then if they want to change DEs, will install LXDE. As I said, just curiosity. The nice thing about Linux is you are free to make just about every combo you like.

---

### Post by herqulees on 2013-10-28
> **DuckHook said:**
> Just a curiosity question...

Why Compiz? Most people who install Lubuntu do so because they *don't* want Compiz. Those who want it tend to install Ubuntu, and then if they want to change DEs, will install LXDE. As I said, just curiosity. The nice thing about Linux is you are free to make just about every combo you like.

Found this thread in search when I was just looking to see what people were talking about with Lubuntu since I have yet to try it, waiting on it to download. I like *buntu because it's become near rock solid and pretty much everything just works, yeah I have to get into the command line sometimes still (Bumblebee and TLP setup) but over all I can install it and just use it nowadays. But in my opinion Ubuntu has become bloated with their philosophy on having an operating system install with all the types of programs most people need, with programs that most people have never heard of. Not trying to put Ubuntu down trust me I love it, but I want a properly running bare bones operating system that I have to install what I need and can uninstall what I want, many things in Ubuntu that I don't need programs that I do need somehow depend on them, leaving me stuck with them wasting space. I tried using the Ubuntu mini CD and just installing Xfce4 and later using "apt-get install xubuntu-desktop --no-install-recommends" but both left many system related things missing or broken taking me away from the *buntu stable and complete OS feel. So I figure I have two options, see how this Lubuntu with LXDE is, or go back to the --no-install-recommends method and learn more about the inner workings of the OS to get things working my way.

---

### Post by vasa1 on 2013-10-28
@herqulees, this is a support area of the forum where people address specific support questions asked by the starter of the thread. There are other areas, listed on the forum's main page, for the type of post you've made.

---

### Post by pgradone on 2013-11-03
> **DuckHook said:**
> Just a curiosity question...

Why Compiz? Most people who install Lubuntu do so because they *don't* want Compiz. Those who want it tend to install Ubuntu, and then if they want to change DEs, will install LXDE. As I said, just curiosity. The nice thing about Linux is you are free to make just about every combo you like.

-------------------------------------------------------------

- I think quite the contrary.
Since compiz uses a lot of resources, wouldn't it be faster wile running on a low-resources consuming desktop such as LXDE?
I have an old Acer EeePC where I would like to run *buntu with compiz effect, but Unity would be a bit too heavy on it.
Therefore, the logical combination for that would be Compiz+LXDE, i.e. LUbuntu with compiz.
The fastest thingy I could make run on little EeePC until now is Knoppix (has LXDE+compiz) which unfortunately is not as supported as *buntu. :(

---

