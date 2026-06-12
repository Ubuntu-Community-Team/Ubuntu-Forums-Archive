---
title: "Where is gnome?"
date: 2008-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xlh1000 on 2008-10-16
I am totally new to ubuntu.

 

I have installed the latest version of ubuntu.

 (8.04.1 LTS Hardy Heron).

I was trying to install a dial up internet account and read that gnome-ppp was the prefered way to do this.

I have looked for gnome every where and the only reference to it is 'about-gnome', which needs an internet connection.

Its not in applications, so i tried terminal.
First i typed in "startx", but it said 'user not authorized to run the x-server....aborting.

So then i tried "/etc/init.d/gdm start"
That said 'starting gnome display manager... open:  permission denied        [fail]

So here i am, looking for the 'roaming gnome'.:lolflag:

Do i need to do a re-install, or am i missing something real obvious here?:confused:

---

### Post by 73ckn797 on 2008-10-16
Most terminal commands require root permissions. That is obtained by first typing "sudo" before any commands. Try that and also reference "man man" via terminal. That is the command reference manual. There you will learn a lot.

Try this and look around: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by Patb on 2008-10-16
> **73ckn797 said:**
> Most terminal commands require root permissions. That is obtained by first typing "sudo" before any commands. Try that... 
No, use "sudo" only where it is required. If it is needed, you will be prompted with a message. I like the prompt message which says: "Since GParted can be a weapon of mass destruction only root may run it" because that says it all. It is easy to mess up settings and permissions if you use sudo (ie root) when it is not required. Amen. ;)

Anyway, welcome to the forum, Xlh. Have you got a gui interface going? If so, Gnome is installed okay.  If not, you should either reinstall Ubuntu or look at getting GDM and Gnome installed before you worry about dialup. Search the forum first. 

For the dial up question, you use Synaptic to install things (System > Administration > Synaptic) and find "gnome-ppp", right click and install. 

Here again, search the forum. There is a lot on dial up and several alternative ways to get it going.

Cheers, Pat.

---

### Post by xlh1000 on 2008-10-17
THANK YOU PATB AND 73CKN797.
Now that i have some solid direction to look in, maybe i can get this working. :)

---

### Post by 73ckn797 on 2008-10-17
> **Patb said:**
> No, use "sudo" only where it is required. 

OPPS! I was assuming too much.

---

### Post by Patb on 2008-10-17
No worries, 73ckn797. Sorry to risk confusion. I just thought that advice on 'sudo' should be qualified, especially for a first poster. :)

Xlh1000, if you have difficulties with dial-up, I forgot to give the link to the community documentation at [https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex). You will see there are lots of articles on dial-up there.  

If you can't find what you need there or in this forum, please post with a detailed description.

Good luck, Pat.

---

### Post by xlh1000 on 2008-10-21
I went into synaptic to install "gnome-ppp" but it was not in there.There was a bunch of things 'gnome related' but not -ppp.
Everything could only be marked to remove.

---

### Post by Patb on 2008-10-22
Xlh, I'm not sure but it sounds like you might need to read up on Synaptic. 
> I went into synaptic
How? If you are starting synaptic from a terminal, type "gksudo synaptic" not just "synaptic". This program does need administrative privileges to actually install anything.
> Everything could only be marked to remove. 
Do you have all packages shown? Click on "All" in the top left window. 

Have you got the Universe repository enabled? (Settings > Repositories). Then you MUST click "Reload" before continuing. (Mind you, this will require that you have an internet connection and I'm not sure you have).

If you cannot find gnome-ppp after checking those things, please repost with a detailed description of what you have tried. 

Sorry if I'm sounding like a machine gun with these questions. Good luck.

Cheers, Pat.

---

### Post by Kevbert on 2008-10-22
Have you seen this [[COLOR="Red"]page[/COLOR]]("https://help.ubuntu.com/community/DialupModemHowto") for dialup ?

---

