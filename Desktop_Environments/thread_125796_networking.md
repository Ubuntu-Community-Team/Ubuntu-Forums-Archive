---
title: "networking"
date: 2006-02-04
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-04
i never have really bothered or even looked into this before... but now i wanna know is it possible and how to do it 'networking with windows that is'

basically i want to know if it is possible to get on the network of a windows system and if i can veiw file etc etc... if u can how do i it

workgroup = workgroup
ip specifications

gateway 192.168.254.254
subnet mask is defualt/wat ever u get wen u just click it

thats it i think... if i anyone can tell me how i wuld like to know

---

### Post by Ramses de Norre on 2006-02-04
I simply clicked "Network Servers" in the places menu.
The windows network was shown then and I could just acces all the windows machines.
I have got a link to them at my desktop and in the nautilus side-panel automaticly ever since.
Don't know whether it's always that simple..

---

### Post by moephan on 2006-02-04
Yes! If you the Ubuntu machine is on the same network, as in connected to the same router, you will most likely be able to just choose Places->Network Servers in Ubuntu and automagically get to the Windows machines there. 

If you want to be able to go the other direction, browse the Ubuntu computer from the Windows machines, that's slightly more involved. There is a program called Samba that can be easily installed by synaptic. It takes a little bit of configuration and tweaking.

Check out Ubuntuguide for more info, epecially on Samba:
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)

Cheers, Rick

---

### Post by ESPOiG on 2006-02-04
well that was easy :P... i never bothered tryin it :P

---

### Post by Ramses de Norre on 2006-02-05
Hmm seems now it's a little less simple.. I had never actually needed any file from the windows computer but now I tried and got a window asking for a user name and password. So I just gave in the username and password from one of the users on the xp machine but that didn't do the trick, the window just reappeared..
I neither can acces the files from users without a password.
What could be holding me back?
I attached a screenshot of the window I always get.

---

### Post by moephan on 2006-02-05
I'm not an expert in interacting with Windows, but here is what I would try:

1. Try setting up sharing on the folder on the Windows machine. I think you right click on the folder that you want to share, pick properties, and there is a tab called Secruity or Sharing
2. Are you sure that MSHOME is your domain? That sounds more like a workgroup to me. Go to the Windows computer, click the start menu, right click on My Computer, and pick properties. There is something called Network Name or something like that that will tell you the domain it's in (I think).

Cheers, Rick

---

### Post by Ramses de Norre on 2006-02-05
sudenly I can just enter all the directories without being promted the window..
I didn't change anything..
The dir's I can see are the ones that are shared.
I'll check the domain name tomorrow, I can't acces that machine directly now.

---

### Post by ESPOiG on 2006-02-08
that is just a windows xp prob

it happens sumtimes in windows it self, such as wen networkin 2 comps for my friend even though everything was fresh reinstall and i set it up as it needed to be... no firewall... folders shared etc ect

it still asked for a password from one comp and then wen i connected usin there old 2k machince and a laptop with xp it had no prob

so i dunno but wen i try it in ubuntu... (with my machines that is) i get the same prob but i just click cancel and it still work :P

---

