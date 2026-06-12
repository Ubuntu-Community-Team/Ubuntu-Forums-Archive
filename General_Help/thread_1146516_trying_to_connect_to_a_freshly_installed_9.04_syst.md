---
title: "trying to connect to a freshly installed 9.04 system"
date: 2009-05-02
forum: General Help
---

### Post by ffxigotenks on 2009-05-02
I finished installing Jaunty on my desktop and then immediately had to leave, so I didn't have time to install anything, I was wondering if there are any base-install ways to say... install a telnet server so I can access it properly, will provide any information necessary

---

### Post by prem1er on 2009-05-02
You probably don't want to use telnet as it sends packets unencrypted, but an SSH server is probably what you want.  Very easy to install and configure.  Here is a link [https://help.ubuntu.com/7.04/server/C/openssh-server.html](https://help.ubuntu.com/7.04/server/C/openssh-server.html)

---

### Post by geirha on 2009-05-02
A fresh install with no modification should be impossible to access from the outside. There's a VNC server installed by default, but it is deactivated by default. To activate it, you'll need physical access to the machine, and go to System -> Preferences -> Remote Desktop.

I'd recommend against using telnet since the password will be sent in plain text. Instead I'd install [openssh-server](apt:openssh-server), after which you can connect to your machine with an ssh-client. An ssh-client is installed in Ubuntu by default, and you type ```
ssh user@host
``` in a terminal to connect. If you want to connect from windows, putty is a popular ssh-client to install.

---

### Post by ffxigotenks on 2009-05-02
*sigh* looks like I'll have to wait until I get back home... thanks for the suggestions though:guitar:

---

### Post by joeinbend on 2009-06-30
Hi all,
I have the same situation as the original post describes, and I didn't see the question answered 100% directly, so I thought I'd "bump" this thread: Started my install (9.04 desktop) on a test machine in my home lab as I was running out the door, and was hoping there would be a way in, weather secure or not.  I also realize that this would be somewhat of a security hole if there were, but if either telnet or ssh are alive and will prompt for a password, then there's really not a security issue. Anyway, any thoughts would be great.. otherwise I'll just install openssh-server when i get home, as usual :)

---

### Post by t4thfavor on 2009-06-30
Without physical access to the machine, you will not be able to spawn a remote terminal session with anything short of a security vulerability. Best case call your mom, and ask her to install openssh-server. Thats what I always do anyways.

Is that direct enough?

I find hands on-site are a valuable asset in any event.

---

### Post by joeinbend on 2009-06-30
ha! thanks for the reply t4thfavor :) Fortunately for my sanity, I do not live with my mom! However about 1:30pm when my 14-year-old finally wakes up, I'll send his butt over to my computer room and put him to work.

cheers :)

---

### Post by t4thfavor on 2009-06-30
Bah, what kind of parent are you if you won't wake up a 14 year old before 1:30 to do wome real work!  In my day we had to get up BEFORE NOON, and we had to make our beds :)

Seriously though, wake his little but up, and put him to good use!

---

### Post by joeinbend on 2009-06-30
lol :) He can get my SSH installed _before_ he mows the lawn... have to have the priorities striaght! thanks for the feedback, was just hoping for a last-ditch effort before having to tell the boy where I hide the keys to my server room ;)

---

### Post by t4thfavor on 2009-06-30
ouch, I got a keypad for mine that logs entry and pin, so I have different pins for everyone. voila nobody in there when there not supposed to be. But everyone can in case they need to.

---

### Post by joeinbend on 2009-06-30
Now that's the way to go! Hmmm.. I've got some RFID goodies laying around, maybe I'll put together a keycard access for it. Oh goodie another project!!

---

### Post by geirha on 2009-06-30
> **joeinbend said:**
> Hi all,
I have the same situation as the original post describes, and I didn't see the question answered 100% directly, so I thought I'd "bump" this thread: Started my install (9.04 desktop) on a test machine in my home lab as I was running out the door, and was hoping there would be a way in, weather secure or not.  I also realize that this would be somewhat of a security hole if there were, but if either telnet or ssh are alive and will prompt for a password, then there's really not a security issue. Anyway, any thoughts would be great.. otherwise I'll just install openssh-server when i get home, as usual :)

Well, if you find yourself installing Ubuntu at another time, enable remote desktop in the live session before you start. System -> Preferences -> Remote Desktop. Then you can check in on how the installation goes remotely, by connecting with a vnc client. Once installed and rebooted though, you're locked out again... unless you chroot into the new system and install openssh-server before you reboot :)

---

### Post by joeinbend on 2009-06-30
Hey that's a great tip! I have another machine I need to load up later this week so I'll try that as a test, and sneak openssh-server in at the last minute. I'll post my results.

---

