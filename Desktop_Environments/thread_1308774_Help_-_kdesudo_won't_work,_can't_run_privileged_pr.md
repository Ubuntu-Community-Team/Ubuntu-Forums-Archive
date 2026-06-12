---
title: "Help - kdesudo won't work, can't run privileged programs"
date: 2009-10-31
forum: Desktop Environments
---

### Post by rma88 on 2009-10-31
Hey everyone, I'm having an issue here. kdesudo is a frontend for sudo, that apps like firefox etc... will run to do administrative commands (like updating etc)

Okay... I can 'su root', enter password, and now I am root. So i obviously know the correct password.

However, when kdesudo pops up to do anything, in this case an update to firefox, i enter the password and i get - "Incorrect password, try again"

what the heck! I can't do anything that requires administrative privileges in KDE? I get prompted, then it says the password is wrong. I only have 2 users, root and myself. soooo... i have no idea what password it's wanting to receive.

Please guys, any help would be really appreciated. This is a pretty annoying one...

Thanks!

---

### Post by sickly on 2009-10-31
thats weird, never experienced that before. Did you try to open a terminal and type

sudo passwd

and then change your password, hopefully it might work.

---

### Post by rma88 on 2009-11-01
well sudo passwd would set my password, and kdesudo expects the root by default. even changing both user's password, kdesudo still asks for the password, then tells me its wrong.

thanks for the responce, anyone else? any help is really appreciated.

---

### Post by gnu-buntu on 2009-11-01
I think the earlier question was whether you can successfully run ordinary sudo on any command?  It's my understanding that kdesudo simply runs sudo for graphical stuff.

Also, you mind find this page helpful; it tells how to repair problems with sudo: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by rma88 on 2009-11-01
yes i can run sudo, in fact i can 'sudo kdesudo ...' and run the command that it is not allowing me to run.

i don't want my user user to be in the sudoers file however, so i will take it out as soon as i can. BUT, the user is in there at the moment, and it doesn't work.

to make things worse, the passwords to my accounts keep changing. it seems i can 'su root', enter password, and be good for a while. a bit later, or after restart i 'su root' and the password is different and thus in correct.

i just restarted and both my root and my users account had a different password. i just had to boot to CD and change the /etc/password, shadow, shadow- files....

what is going on?!?!

im really confused guys, about to just reinstall kubuntu.

any help is really appreciated.

---

