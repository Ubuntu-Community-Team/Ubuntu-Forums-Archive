---
title: "Beryl has stopped working"
date: 2007-02-06
forum: Desktop Environments
---

### Post by PaulFXH on 2007-02-06
Using a Dell Dimension E520 with a nVidia GeForce 7300 LE graphics card.
Installed Beryl from [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) about  4 days ago.

Although I had some problems with authentication of some of the new repositories Beryl worked well after the installation. 
Nevertheless, one problem I had was that if I started the session with XGL selected, Beryl would not work. Only when I selected GDM in the session options could I then use the gem>Select Window Manager to select Beryl and then Beryl worked. And indeed, it did work very well......until yesterday, that is.
When i booted up yesterday, Beryl just could not be persuaded to start. Selecting Beryl as the Window Manager made no difference. It seemed that Beryl was starting up (a lot of shaking of windows occurred) but then crashed which brought me back to GDM.

I then found that I had lost direct rendering so I re-loaded the nVidia driver and it came back but Beryl did not. same behaviour.

OK, so getting desperate now, I re-installed Ubuntu and subsequently went through the same guide to install Beryl again. I still had the same problems with validating some of the repositories but the rest of the installation was smooth.
But Beryl still won't work.

Typing beryl in the Terminal tells me it is Checking  for XComposite extension : failed
No composite extension.
I have seen from the forums that this problem has been resolved for others by including in the xorg.conf the line Options "Composite" "Disable" in a new Extensions section.
But once again, this gave no improvement for me.

I'm sure the solution to this is simple but I just can't seem to be able to track it down.
Can anybody help?

---

### Post by shareMenaPeace on 2007-02-06
I dont think you need to reinstall ubuntu i had trouble too and wrote a small guide on how to uninstall beryl. 


[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)
Do not use this guide to install beryl again.

Maybe you didnt added the correct repos or the correct repo key?
Checkout the other guides - specialy on repos and repo authentication key after you uninstalled beryl.
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by PaulFXH on 2007-02-06
Thanks for your reply.
I tried your uninstall guide and re-installed using this also.
However, no major improvement.

The only positive difference is that the Beryl radio button in Select Window Manager does actually stay selected now.
However, beryl is still not working.

Indeed, things are actually worse than before in that the Terminal window instead of being the wobbly brightly decorated window it was at the weekend when beryl worked, is now actually TOTALLY white with nothing whatsoever visible even when I try to type.
Thus I now cannot use Terminal.

Looks like I'm going to have to uninstall beryl again.

Any further comments?

Paul

---

### Post by PaulFXH on 2007-02-06
Just an addendum to my last post:

I can now actually use terminal if I select Metacity as the Window Manager rather than Beryl.
Additionally, beryl DOES actually work to some degree now in that I can get the cube to rotate which I positively could not do this morning.

What appears to be wrong now is simply that any windows I call up (such as Terminal or a text editor) are totally devoid of any themes or borders or indeed (in the case of the Terminal) of anything at all.

This is in spite of me having chosen an Emerald theme but it just doesn't seem to have been adopted for whatever reason.

Therefore, the "fix" that shareMenaPeace suggested has actually brought me quite a way forward but still some little stretch to go.

Any further help/suggestions/comments???

---

