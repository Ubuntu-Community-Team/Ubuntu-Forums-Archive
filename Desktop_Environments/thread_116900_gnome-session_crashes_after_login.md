---
title: "gnome-session crashes after login"
date: 2006-01-13
forum: Desktop Environments
---

### Post by maqua on 2006-01-13
when i try to normally start a gnome session ubuntu tells me only that the session was shorter then ten seconds and in the terminal report it says something about not finding tcp. 
I would copy and paste the report but somehow it doesn't work.

I am only able to start the failsave terminal, from which i then can start a gnome-session which works.

I know it is not a good description, i will try and write down what ubuntu says and then post it. But till then if anybody has an idea i would be very happy!

Thank you very much
maqua

---

### Post by ahave2005 on 2006-01-13
It could be ICEAuthority thats your problem. It should be a bug, but isn't, since its a common error.

When you boot, you problably get to a terminal here you do:
> sudo chown yourusername .ICEauthority

.
You might be able to do:
> startx
otherwise reboot.

It's an iritating problem, that occurs when user root overwrite .ICEauthority with his own credentials. I don't have the reason, but it does sometimes.
/ahave

---

### Post by maqua on 2006-01-13
thank you!
i tried it directly out but it says

   root@paradise:/root# sudo chown martin .ICEauthority
   chown: cannot access `.ICEauthority': No such file or directory

but i tried it from a terminal that i opened in the gnome-session, maybe that is a problem?

maqua

---

### Post by maqua on 2006-01-13
Ok this time it worked!!!

thank you so much!! 

that was my first time i posted a question and within 5 minutes the problem was gone!!! 

This forum is great thanks very very much!

maqua

---

### Post by ahave2005 on 2006-01-13
Every new user is a contribution to the linux community. Don't forget ubuntuforums.org.
All the best.
/Ahave

---

### Post by qferret on 2006-01-14
The reason (Somewhat):

Not really sure WHY, but it usually happens when running a GUI app as root. I did it a couple of times after running "sudo k3b" because I was too lazy to change the permissions on the files I wanted on the CD  ;-)

---

### Post by qferret on 2006-01-14
err...wait....  mine was .Xauthority, but I think it's the same situation....

---

