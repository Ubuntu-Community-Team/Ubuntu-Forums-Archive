---
title: "Can desktop effects be used from virtualbox"
date: 2009-01-29
forum: General Help
---

### Post by wolterh on 2009-01-29
**BACKGROUND**
I've always wanted to merge Windows' ability to run the latest game, with the functionality and comfort that Ubuntu gives me, without having to dual boot. So, I found out about virtual machines; I thought, "Great! Now I will be able to run Windows from Ubuntu, and maybe even play 3D games that Wine can't handle!", but no, I found out afterwards that you couldn't do that. At least not flawlessly. Some days later, I figured out "How about doing the opposite thing: running Ubuntu from Windows? The only graphic need that Ubuntu has would be compiz, but as Virtualbox has 3D acceleration for OpenGL, that'll do".

**THE PROBLEM**
It does not. I can't run compiz from my Virtualbox, so here I wait for somebody to come and contradict me.

---

### Post by wolterh on 2009-01-29
Update: I ran the compiz-check script and it gave me a [ [COLOR="Orange"]WARN[/COLOR] ] on the hardware/setup section. Then I knew it was because my drivers where not known by the system (that's because I use virtualbox's drivers). Afterwards I told compiz-check not to care about that,  and it gave me an [ [COLOR="Lime"]OK[/COLOR] ] for everything.

Nonetheless, I am still not able to run the Desktop Effects.

---

### Post by greyfox1 on 2009-01-29
What version of VirtualBox are you using?  Beginning only with Sun's 2.1 version, there is available support for hardware acceleration.  I don't know the specifics but this is a new feature (2.1 just came out last month).  Hope that helps.

Also, running Windows as the guest system under Linux is a bad idea for gaming due to all the overhead needed-- you're essentially running two operating systems simultaneously with the same hardware, which can really eat up your resources.  Also, the guest OS typically can only have access to a fraction of the total system memory / video memory as well.  All of this is bad for gaming.

Ultimately if you want to maximize performance, the best (if not most convenient) solution would be dual booting if WINE isn't good enough for you. Running Linux full-time as a guest OS just wouldn't be as nice as booting into it (IMO) and using a virtual Windows installation is just a bad idea with respect to gaming.

---

### Post by wolterh on 2009-01-29
Well, that's why I chose Windows as the host OS. Now, I have 3D Acceleration enabled and gave 64MB of Video Memory, should I give it more memory in order to be able to run compiz?

---

### Post by Tubes6al4v on 2009-01-30
I am in the Dual boot camp. I have some games and whatnot on windows, and everything else in Ubuntu. It can be annoying to switch, but just get the two booting quickly and it isn't so bad.

Alternatively, have you tried using Wubi to have Ubuntu in windows? You may be able to do desktop... Oh damn, you have to reboot for that. Hmm, sorry!

---

### Post by greyfox1 on 2009-01-30
Unfortunately I'm not sure if the details as I haven't tried this out myself yet, but [here]("http://www.phoronix.com/scan.php?page=news_item&px=NzAyNA") is an article on this functionality with some further details and a few links to check out.  Hope this helps!

---

### Post by wolterh on 2009-01-30
Man, that's awesome! I think I can get this thing to work!
I understand is not quite finished, right? Look at this picture and decide for yourself, [http://www.virtualbox.org/attachment/ticket/2940/chromium_wined3d.jpeg](http://www.virtualbox.org/attachment/ticket/2940/chromium_wined3d.jpeg)

Ok, in summary, all I have to do is install OpenGL on the guest, plus compile and install wined3d.
Seeing it this way, I think it might be even wiser to run windows as the guest, now that my vista installation eats up 1.35GB of ram all by itself, so I would be using less ram if I ran a windows xp guest system under ubuntu. Now, I understand as well that all the work will be in fact channeled to the GPU, replacing the need of a powerless virtual video card.

---

