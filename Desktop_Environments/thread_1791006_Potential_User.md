---
title: "Potential User"
date: 2011-06-26
forum: Desktop Environments
---

### Post by Maverick494 on 2011-06-26
Perhaps this better belongs in general, but I will start here and if a MOD needs to move it good deal.

I have been trying hard to get into linux.  I am an above average windows user, some small amount of programming and a bit of dos/network experience.  One of the things I am looking for to help me get into linux is for the distro to "just work."  For me windows has never not just worked, I have done some things that have caused issues to my windows and I have fixed those issues as well.

Another thing I am looking for is something that looks at least somewhat similar to the windows desktop in order to make the transition as easy as possible.  In addition the distro has to play WoW at a minimum.

I am very open to suggestions.  I tried ubuntu and kubuntu briefly, but had a hard time getting wine to work with Rift (I am not longer playing rift) and I would like something that makes gaming possible.

---

### Post by tgm4883 on 2011-06-26
> **Maverick494 said:**
> Perhaps this better belongs in general, but I will start here and if a MOD needs to move it good deal.

I have been trying hard to get into linux.  **I am an above average windows user, some small amount of programming and a bit of dos/network experience.**  One of the things I am looking for to help me get into linux is for the distro to "just work."  For me windows has never not just worked, I have done some things that have caused issues to my windows and I have fixed those issues as well.

Another thing I am looking for is something that looks at least somewhat similar to the windows desktop in order to make the transition as easy as possible.  In addition the distro has to play WoW at a minimum.

I am very open to suggestions.  I tried ubuntu and kubuntu briefly, but had a hard time getting wine to work with Rift (I am not longer playing rift) and I would like something that makes gaming possible.

I'm doing a bit of research and was hoping you could define the above bolded section for me.

---

### Post by doas777 on 2011-06-26
welcome op.

I think you will rather like ubuntu, but I would recommend dual booting if you are interested in playing windows only games. Ubuntu exposes a great deal more of its guts than windows does, so getting used to it is a great learning experience for those that love computers, and in learning it, you gain a more fundamental understanding of what computing really is, beneath what the ui designers want you to see. 

for many people ubuntu does "just work", but I think that that is a highly subjective statement. the question is, does ubuntu just work for you. try it out.

good luck and happy ubuntuing,

---

### Post by Maverick494 on 2011-06-26
> **tgm4883 said:**
> I'm doing a bit of research and was hoping you could define the above bolded section for me.

I have setup home networks and worked with some windows servers and cisco routers.  Its limited experience.  basic dos recovery commands and other shell commands.

There aren't too many windows issues that are unrecoverable from an average user that I can't usually fix with a few commands in the recovery console.  

I took C++ and general programming classes (though it has been a while), I have done some HTML, XML, and Javascript.

---

### Post by Maverick494 on 2011-06-26
> **doas777 said:**
> welcome op.

I think you will rather like ubuntu, but I would recommend dual booting if you are interested in playing windows only games. Ubuntu exposes a great deal more of its guts than windows does, so getting used to it is a great learning experience for those that love computers, and in learning it, you gain a more fundamental understanding of what computing really is, beneath what the ui designers want you to see. 

for many people ubuntu does "just work", but I think that that is a highly subjective statement. the question is, does ubuntu just work for you. try it out.

good luck and happy ubuntuing,

There in lies the problem, 98% of what I want to do, ubuntu does just work.  Its the gaming that makes it a sticky situation.  I have heard its possible to game on linux.  I also don't want a desktop environment that is so different from windows that it makes the switch daunting.

---

### Post by doas777 on 2011-06-26
> **Maverick494 said:**
> There in lies the problem, 98% of what I want to do, ubuntu does just work.  Its the gaming that makes it a sticky situation.  I have heard its possible to game on linux.  I also don't want a desktop environment that is so different from windows that it makes the switch daunting.

ok, here is my experience, your mileage may vary. just a personal tesimonial.

running windows games in ubuntu is tricky at best and usually requires some wrestling with the system. importing dlls and setting up app profiles in wine, gathering x64 depends and compiling emulators, tweaking VMs, etc. sometimes you just have to give up.

Wine:  wine plays exactly one game that I do: civ4. most of the others I've looked at are rated bronze or garbage. always check the appdb at winehq.org.

Emu: some emulators run fine with a simple apt-get install, but others have performance issues. I've tried compiling the latest and in some cases its worked marvelously, but in others, finding x64 versions of the dependencies was impossible. I managed to get pcsx2 compiled up, but it never performed as well on ubuntu as it did in windows, even when compiling the same version on the same hardware.

VMs: Ive been able to get some of my old favorites running in VMs on both VBox and VMWare Player\workstation. VMWare does seem to have better  3da for their drivers. if the game will play in dx9 you have a good chance of it working in a VM. Netflix is another thing that generally works well in VMs.

in the end, dualbooting is by far the best option, unless you are trying to give yourself a challenge. Some folks use PlayOnLinux or Cedega or winetricks or whatever, but I can give no real advice on them. check em out to see if they are for you.

---

