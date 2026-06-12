---
title: "White Screen of Death"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by icarustwo on 2007-04-25
My apologies if this has been dealt with a thousand times over and over.

I am a complete nublet when it comes to nix / linux / ubuntu / gnome.

I just installed Feisty server version and used apt-get to install "ubuntu-desktop".

I have been a Windows user for years, but I am trying to learn nix and i thought ubuntu was a good place to start as I have heard great things.

Trouble is, being one of those that jumps for nifty gimmicks straight away, i ignored the warnings and enabled desktop effects straight away.

the screen went white and is no forever white when i log in.

well first it goes black / white, then the contrast is reversed and then it's all white.

I have tried pressing ctrl+alt+f1 to run the terminal and then typing:

sudo apt-get remove --reinstall --purge desktop-effects
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

but still no dice.

can anyone shed some light apart from completely removing ubuntu-desktop?

many thanks for any help you can offer.

Gregory

---

### Post by bas1 on 2007-04-25
I had the same issue before. I do not have any idea on what causes it, but I do know that re-starting the X server should fix this. Try Control-alt-backspace. That will restart the X server.

---

### Post by icarustwo on 2007-04-25
thank you

i will try that now -

tried it, goes back to the log in screen.

doesn't work ! arrgggghhh

it's a pretty old PC so i guess thats why it broke / bad drivers, but I can't get in to configure it. Is there any way I can flag desktop effects of from the terminal?

---

### Post by Gmaster1440 on 2007-04-25
> **icarustwo said:**
> thank you

i will try that now -

tried it, goes back to the log in screen.

doesn't work ! arrgggghhh

it's a pretty old PC so i guess thats why it broke / bad drivers, but I can't get in to configure it. Is there any way I can flag desktop effects of from the terminal?


I had the same problem too. Why it happened to me is that i was running it on a laptop and the graphic card that it had was some sort of integrated "intel" driver that isn't supported. What that means is that the drivers in your computer are either out-of-date or simply not supported. 

P.S. Also check your repositories

---

### Post by dreamsayer on 2007-04-26
I had the same exact problem after turning on 3d and after I rebooted my machine. Clean new Ubuntu install btw. Upon a restart a black box with white center and then the screen went completely white. Ctrl-alt-backspace or a sudo-dpkg-reconfigure did not fix it. I installed the nvidia supplied restricted drivers. Since nobody seems to know how to fix this, I'm pretty much going to skip using this release of Ubuntu for now. The quality of this release seems very very poor.
   
> **bas1 said:**
> I had the same issue before. I do not have any idea on what causes it, but I do know that re-starting the X server should fix this. Try Control-alt-backspace. That will restart the X server.

---

### Post by speeddemon8803 on 2007-04-26
Giving up so soon?

For your information..there are probably thousands of people that are having your problems..just havent figured out how to take the left turn on Help AVE. I wouldnt give up if I were you buddy, someone will eventually help you out! As for me, you've stumped me..as I am not yet upgraded, im actually going to attempt to recreate the bug..as I have a laptop i really dont need anymore...if it crashes..ah well..but if i fix whats going on..back to here I go..and ill post my results.

Have a nice day! Keep Ubuntuing!

---

### Post by dreamsayer on 2007-04-26
I'm not giving up. ;) I want my linux os to boot so I can use my computer. If it's crashing to the point of unusable/reliable, there are plenty of alternatives...
  
> **speeddemon8803 said:**
> Giving up so soon?

For your information..there are probably thousands of people that are having your problems..just havent figured out how to take the left turn on Help AVE. I wouldnt give up if I were you buddy, someone will eventually help you out! As for me, you've stumped me..as I am not yet upgraded, im actually going to attempt to recreate the bug..as I have a laptop i really dont need anymore...if it crashes..ah well..but if i fix whats going on..back to here I go..and ill post my results.

Have a nice day! Keep Ubuntuing!

---

### Post by AVH on 2007-04-26
I got my white screen by un-checking the Nvidia drive in the restricted drivers section of the System menu and then following the instruction to reboot so that the new settings could take effect. Big mistake. Is there anything short of a re-install that will fix this?

How would I go about reloading a video driver form the command line of the rescue boot option?

---

### Post by nitsnipe on 2007-04-27
OK, the problem is that compiz does not revert back to deault settings after is  fuks up. But I don't know how to dissable desktop effects through the command line.                    Another way to do this is to do it blindly,   this indeed sounds rlly silly, but it should work, because everything is working fine except that you're seeing a white screen.   

You could try using keyboard abd mouse to click on desktop effects and then press enter to disable them.    But i gotta see this on another ubuntu system and remember how many times to click the arrow keys and when to press enter.

---

### Post by fwojciec on 2007-04-27
What video card do you have?  Perhaps the easier solution to your problem would be to configure xorg.conf correctly so that the desktop effects work (so that you can switch them off using GUI if you wish).

---

### Post by AVH on 2007-04-30
> **fwojciec said:**
> What video card do you have?  Perhaps the easier solution to your problem would be to configure xorg.conf correctly so that the desktop effects work (so that you can switch them off using GUI if you wish).

I have an nVidia GeForce MX 440. I already had desktop effects off in the system menu , after triying them for a whille(The wobbly window made me dizzy). I turned the nVidia restricted driver off because I was still have window display problems, i.e. buttons or the top of the window were missing or garbled.

---

### Post by petur on 2007-05-03
**help** I'm stuck at the same point... all I see is linux guru's lauging at newbies about their problem.... doesn't anybody know the solution?

please...

---

### Post by grumpymole on 2007-05-08
AVH,

I had the same as you - white screen after disabling the proprietary Nvidia drivers.  To fix it, I booted into a failsafe terminal session and then ran > sudo apt-get install nvidia-glx  This restored things for me.

Cheers

---

### Post by Derspankster on 2007-05-08
> **nitsnipe said:**
> OK, the problem is that compiz does not revert back to deault settings after is  fuks up. But I don't know how to dissable desktop effects through the command line.                    Another way to do this is to do it blindly,   this indeed sounds rlly silly, but it should work, because everything is working fine except that you're seeing a white screen.   

You could try using keyboard abd mouse to click on desktop effects and then press enter to disable them.    But i gotta see this on another ubuntu system and remember how many times to click the arrow keys and when to press enter.

Boot into terminal or command line and run dpkg-reconfigure xserver-xorg.  Remove glx from Section Module by arrow keying down to it and pressing your spacebar. That will remove the check from glx. Finish the rest of the screens and restart your system. The white screen should be gone.

---

### Post by AVH on 2007-05-11
Grumpymole, Derspankster.
Thanks guys. I hope this helps others. I, unfortunately,  lacked  patience and re-installed (Edgy!!) before you replied. But, finally, there is a solution posted for what is a  a really easy trap to fall into. Is there a bug posting on this? Shouldn't there Be?


Thanks again

---

### Post by soro2005 on 2007-06-05
Not solving the problem with the Xserver setup, but shooting down Desktop effects:

1. Press ctrl+alt+F1 for another terminal (or F2 through F6 if tty1 is busy)
2. log into it with your user + password as prompted
3. shoot down compiz by typing
```
killall compiz.real
```
perhaps preceded by a sudo if it doesn't work otherwise, but it should.
4. go back to your GUI by pressing ctrl+alt+F7
5. you may want to start metacity by typing "metacity" at a command prompt

One of the good things about Linux: If you've screwed up one GUI/terminal/login, you open another one and fix it from there. :-)

---

### Post by hfw on 2007-06-07
I have to thank all who have posted help in this thread.  I was having this problem too, and now I am back up and running.  Glad I found this thread.  Ya'll are great.  As a noob, the community support behind Ubuntu is why I decided to give it a try instead of another distro.

Now I just need to get Beryl back....

Thanks
Hal

---

### Post by leonyi on 2007-08-31
> **grumpymole said:**
> AVH,

I had the same as you - white screen after disabling the proprietary Nvidia drivers.  To fix it, I booted into a failsafe terminal session and then ran   This restored things for me.

Cheers

Same symptom here; however, I got the white screen after enabling "Desktop Effects".  My system is a Toshiba Satellite with an  ATI graphics card.  Since I was running out of ideas, I decided to just iinstall the  nvdia-glx driver,  by running "sudo apt-get install nvidia-glx" at the command prompt, then rebooted and that fixed my problem.  I am now "Ubuntuing" ok.  Finally! :)

---

### Post by lemmy999 on 2007-09-01
Another lifesaver. Thanks for saving me a lot of work.

---

