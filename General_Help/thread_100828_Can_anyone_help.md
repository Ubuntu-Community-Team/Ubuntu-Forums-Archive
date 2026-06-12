---
title: "Can anyone help?"
date: 2005-12-08
forum: General Help
---

### Post by madsalty on 2005-12-08
I have just installed Ubuntu and cannot install anything can somebody please tell me in clear and simple steps how to create? or run as a super-user.

---

### Post by sabitha on 2005-12-08
put the error what you instaled ;)

---

### Post by madsalty on 2005-12-08
do you mean what error comes up? if so it says:

'you need to run this installer as the super-user'

---

### Post by sabitha on 2005-12-08
did you put your sudo comand at the front of comand
ex: sudo apt-get install name_pakages
sory my english

---

### Post by madsalty on 2005-12-08
can you please explain exactly what i have to do

---

### Post by kingsidy on 2005-12-08
open the terminal, then type in: sudo su
it is then going to ask for your root password. Enter that. In the screen you will now see something like: root@ubuntu (see attached picture). Then type in dpkg  -i *name of package*, press enter

---

### Post by Bachstelze on 2005-12-08
Or you can use the more user-friendly Synaptic Package Manager. Go to System W Administation > Synaptic

---

### Post by madsalty on 2005-12-08
This is going to sound stupid but i realy am a noob to linux can you please go through it in simple stages (realy simple)

---

### Post by Bachstelze on 2005-12-08
Click System in the gnome panel, then Administration and Synaptic package manager. It will prompt for your password and then you will be ready to install a lot of software.

---

### Post by sabitha on 2005-12-08
ok now what is you going to install
can you open the terminal (in aplication-->terminal) ?
do what people already said for you
type the code 
$ sudo su

---

### Post by madsalty on 2005-12-08
it doesn't ask me for my password?

---

### Post by sabitha on 2005-12-08
?????????
ok ..... did you she the line like this :

root@ubuntu:/home/admin #

this what i have if i type $ sudo su

---

### Post by Bachstelze on 2005-12-08
sabitha > I disagree with you on this, he's a newbie so he would be more comfortable with Synaptic I think, rather than apt-get or dpkg -i

---

### Post by sabitha on 2005-12-08
ok ;)

---

