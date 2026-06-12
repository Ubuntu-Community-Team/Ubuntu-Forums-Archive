---
title: "My user account is messed up..."
date: 2006-02-19
forum: Desktop Environments
---

### Post by xXx 0wn3d xXx on 2006-02-19
I just reinstalled ubuntu and I used the expert installation. I made a root account and my regular user account. I can login but when I try to do anything I need to be the root. Sudo does not even work. I tried to change my pass by using the passwd <username> command but I still can't use synaptic or anything else...

---

### Post by metwo on 2006-02-19
When you say 'I can't do anything' do you mean you can't do anything that requires sudo (like synaptic)? If so are you in the admin group? The command 'groups' will give you a list of groups you are a member of.

---

### Post by xXx 0wn3d xXx on 2006-02-19
This is what I get with groups: 

chris adm dialout cdrom floppy audio dip video plugdev lpadmin scanner

I just want to be able to sudo

---

### Post by metwo on 2006-02-19
Ok, there's your problem, you need to be a member of the admin group.

As root do,

usermod -Gadmin *yourusername*

You'll probably need to logout and log back in for it to take effect.

---

### Post by xXx 0wn3d xXx on 2006-02-19
I tried that but there is no admin group... how can I create one ?

---

### Post by metwo on 2006-02-19
you'll need to do 

groupadd admin

as root, you might then need to edit /etc/sudoers - do you have sudo installed?

/etc/sudoers should contain the line

%admin  ALL=(ALL) ALL

---

### Post by xXx 0wn3d xXx on 2006-02-19
the sudoers file does not have that line. But it does have

# User privilege specification
root	ALL=(ALL) ALL

should I add %admin ALL=(ALL) ALL under it ?

---

### Post by metwo on 2006-02-19
That should do it, yes.

I'd advise running 'visudo' to do this edit though.

---

### Post by xXx 0wn3d xXx on 2006-02-19
ok I tried these with no luck, 

root@ubuntu:/home/chris# visudo /etc/sudoers
usage: visudo [-c] [-f sudoers] [-q] [-s] [-V]
root@ubuntu:/home/chris# visudo gedit /etc/sudoers
usage: visudo [-c] [-f sudoers] [-q] [-s] [-V]

---

### Post by metwo on 2006-02-19
Just visudo. Nothing more :)

---

### Post by xXx 0wn3d xXx on 2006-02-19
ok, and how do I save it ?

---

### Post by metwo on 2006-02-19
Assuming it says 'GNU nano' in the top left corner you'll want to hit Ctrl-O, followed by Ctrl-X to exit.

edit: you'll need to press enter after the ctrl-o

---

### Post by xXx 0wn3d xXx on 2006-02-19
YES !!! Thank you so much ! It worked. You are by far the most helpful person ever ! :)

---

### Post by metwo on 2006-02-19
[QUOTE=MasterChief1234]YES !!! Thank you so much ! It worked. You are by far the most helpful person ever ! :)[/QUOTE]

Thanks, I try! ;)

---

### Post by Mustard on 2006-02-19
Expert install doesnt give the first user account sudo privileges by default.  That is basically what occured.  Since its an 'expert install', it assumes you have an understanding of how to give superuser privileges to your users (as you have done above).

---

