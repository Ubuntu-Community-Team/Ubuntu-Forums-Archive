---
title: "Radeon Xpress 1100 and Compiz Fusion"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by GameKing505 on 2008-04-09
Hi. I am running Ubuntu Gutsy Gibbon and am trying to get compiz-fusion to work. Right now I think my graphics card is Radeon Xpress 1100, which I heard doesn't play nice with Ubuntu. I am an utter noob but would appreciate some help on getting it to run.

When I try to change the desktop effects from none to normal, I get the message "the composite extension is not available." I am able to get around this by installing xgl, but that is a really crappy solution and is very buggy for me. I am not willing to go THAT far for the nice effects.

What I was wondering however was whether or not a driver existed that would let me run compiz without XGL, possibly with AIGLX? I really have no clue what I'm talking about here but would love some help.

Thanks in advance!

---

### Post by GameKing505 on 2008-04-10
Anyone?

---

### Post by GameKing505 on 2008-04-12
Pretty please with sugar on top?

---

### Post by GameKing505 on 2008-04-14
Thank you very much I appreciate all of your help so very much.

No but really. I'm sure someone knows how to get compiz running with this graphics card. Please help me!!!!!

---

### Post by mrmiserable on 2008-04-14
ok i will try 

firstly the driver in repos (synaptic) uses the 8.37 blah blah this driver needs xserver-xgl

now the latest ati driver  8.3 they have changed the names now to replicate windows numbers can run without xgl 

so your graphics card does not have on the ati site a linux 8.3 driver but i believe your card is an x200 based chipset you could try to install that and maybe that could work

if you need anymore info maybe i can help

i cannot believe nobody has answered you thread

---

### Post by mrmiserable on 2008-04-14
also this link is good use method 2 this will make .deb files that will be easy to uninstall from snaptic if all goes wrong


[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by Zorael on 2008-04-15
Your videocard is not a very common one, so it's not surprising people aren't leaping to help you. Since, by extension, it's not a very common problem. Hmm?

I would suggest you try installing drivers via [Envy](http://albertomilone.com/nvidia_scripts1.html). It is an unsupported script, but it might just get the drivers you want installed. Remember, though, that each time you upgrade your kernel you *will* need to run the script again. It can be run in either a graphical environment or in a terminal.

```
$ sudo envy -t
```

---

