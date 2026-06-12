---
title: "My sound seems low compared to XP."
date: 2009-06-09
forum: General Help
---

### Post by redonwhite on 2009-06-09
Hello,

I recently started playing more games on my XP hard drive.  Everytime i booted up XP my volume would be REALLY LOUD.  I was like "WOOO BOY settle it down now!"  I relized why.  Because everytime i was in ubuntu i had to have the volume cranked up to hear anything.  So when i booted into windows the volume was set extremely loud.  =)  

I have a 5.1 surround sound Logitech wired speaker system.  My motherboard is a GIGABYTE GA-MA790X-UD4 with the on board audio Realtek ALC889A.

Any ideas how to get the volume evened out in ubuntu?

thanks for the help!

---

### Post by ActiveFrost on 2009-06-09
By default it's set to 50% ( the same as for a fresh XP installation ) - pull it up and you'll never face this problem again :p

---

### Post by redonwhite on 2009-06-10
> **ActiveFrost said:**
> By default it's set to 50% ( the same as for a fresh XP installation ) - pull it up and you'll never face this problem again :p

Silly question.  Where the heck are the volume controls?  Thanks for the reply. :D

---

### Post by Polaris96 on 2009-06-10
usually the volume control sits in a taskbar applet.  Otherwise, you can go to system settings / sound.  Also check the app you're running - many have their own internal volume controls

---

### Post by redonwhite on 2009-06-10
> **Polaris96 said:**
> usually the volume control sits in a taskbar applet.  Otherwise, you can go to system settings / sound.  Also check the app you're running - many have their own internal volume controls

Okay so i hit volume control on the task bar.  I already have the bar pushed up 75%.  So i then hit the button "volume control"  Now i get a nice window full of actual volume controls for Master, PCM, Front, Front Mic ect.  At the top it says Device.  I pull down the Device option and am confronted with multiple "mixers".  

Volume still seems low compared to the XP drive.  Its odd.  I dont think i have changed much as far as the volume options in XP either.  Besides telling it that i had a 5.1 system.  

Is there anyway to tell Ubuntu you have a 5.1 system?

Any more suggestions to the volume issue?  

Thanks all!

---

### Post by ActiveFrost on 2009-06-10
[COLOR="Gray"]Sound control can be found on the top right corner ( and again - default settings ), near the clock.
If it's not there, go to System -> Preferences -> Sound ;)[/COLOR]

Just curious - do you need to install any additional drivers ( on Windows XP ) ? As an example, win32 VLC - sound can be increased even if it's already on 100% in your Sound settings. Though, that's just a guess .. :)

---

### Post by redonwhite on 2009-06-10
> **ActiveFrost said:**
> [COLOR="Gray"]Sound control can be found on the top right corner ( and again - default settings ), near the clock.
If it's not there, go to System -> Preferences -> Sound ;)[/COLOR]

Just curious - do you need to install any additional drivers ( on Windows XP ) ? As an example, win32 VLC - sound can be increased even if it's already on 100% in your Sound settings. Though, that's just a guess .. :)

Its possible.  I have been out of the Windows world for some time now.  I only use it for Games.  Theres always tons of drivers needed for everything in windows.  So im sure theres a driver i downloaded at some time for the Realtek audio.

---

### Post by mharrison on 2009-06-10
> **ActiveFrost said:**
> By default it's set to 50% ( the same as for a fresh XP installation ) - pull it up and you'll never face this problem again :p

I noticed when I first installed 9.04 that the volume is set to 50%, but what I am wondering about is this.

When I had windows and had the volume maxed out, the sound was a lot louder where I currently have my speakers set at (my speakers have their own volume adjustment as well), but when I max it out in Ubuntu, the sound is significantly lower.  Might just be me, not sure if there is a fix, but I do find it odd.

---

### Post by Quarkrad on 2009-06-10
Try this - I had problems with sound volume in Ubuntu. Launch the terminal and type in the command:

alsamixer

you should get a graphic window pop up with various volume controls you can adjust.  Use the left/right arrow keys to scroll across and the up arrow to make the adjustments.

---

### Post by mharrison on 2009-06-10
> **Quarkrad said:**
> Try this - I had problems with sound volume in Ubuntu. Launch the terminal and type in the command:

alsamixer

you should get a graphic window pop up with various volume controls you can adjust.  Use the left/right arrow keys to scroll across and the up arrow to make the adjustments.

I'm at work so I can't try right away, but wouldn't Clicking on the Volume Icon on the Panel and clicking Volume control give me the same result?  I used that to max out every volume that I could.

---

### Post by ActiveFrost on 2009-06-10
> **mharrison said:**
> I'm at work so I can't try right away, but wouldn't Clicking on the Volume Icon on the Panel and clicking Volume control give me the same result?  I used that to max out every volume that I could.

Not really ! Alsa is Alsa ( sound "mixer" ) and sound settings are sound settings .. The same as for microphone - you can tweak it through the mixer, not by pulling your main speaker up ( talking only from common sense - haven't done any big experiments with these things ) ;)

---

### Post by mharrison on 2009-06-10
Sounds like a plan...Soon as I can escape the office I'll run home and give it a shot...never hurts to try something you haven't tried before :)

---

### Post by ActiveFrost on 2009-06-10
Check this screenshot below ( made by me a few minutes ago - player default settings ) .. I'm actually scared to pull this up ( as I feel that it will increase the sound by 200% or so ) :D

[IMG]http://i43.tinypic.com/1zv3dkp.jpg[/IMG]

---

### Post by hibliss on 2009-06-10
I would be afraid to pull the volume bar up with the sound playing too :)

On my desktop and notebook that both use Realtek cards, my sound was very low until I cranked up the line in to max. I think the Linux driver confuses line in with something else. Worked on my Eee and my home build.

---

### Post by Quarkrad on 2009-06-10
I found this mixer gave me a sort of system level access that improved the overall volume.  Try it - I am not a unix expert but found it after days of googling - it worked for me.

---

### Post by Dezeo on 2009-06-10
> **Quarkrad said:**
> Try this - I had problems with sound volume in Ubuntu. Launch the terminal and type in the command:

alsamixer

you should get a graphic window pop up with various volume controls you can adjust.  Use the left/right arrow keys to scroll across and the up arrow to make the adjustments.


sorry for OT but,
I have problems with my headphones, and in my alsamixer the headphone number says 0.
do this have anything to do with eachother, or is you'r headphone number also 0, but you have no problems with you'r headphones?

(my problem is that I don't get any sound in my headphones, it simply continues to play trough speakers. (laptop))

thanks for any help, and again, sorry for OT

---

### Post by redonwhite on 2009-06-11
> **Quarkrad said:**
> Try this - I had problems with sound volume in Ubuntu. Launch the terminal and type in the command:

alsamixer

you should get a graphic window pop up with various volume controls you can adjust.  Use the left/right arrow keys to scroll across and the up arrow to make the adjustments.

Hey cool tip thanks.  

Notice there is a Front, surround, and center options. (weird center has a red underline. hmmm)  All three of these are at 0.  My master is at 85.  gonna have to test out the surround option later.

---

### Post by Stargazer989 on 2009-07-18
I'm having the same issue on my desktop, but for some reason not my laptops(on my gateway laptop i actually turn it down to 50% for a 'full' effect. past 50% and it's like "IT'S GONNA BLOW"). i do have an audio card as well as the CD that came with the card. do i need to install something ? the card is a "Creative Labs CA0106 Soundblaster" ( obtained from 'lspci' )

---

### Post by naklinaam on 2009-07-18
Hi,
I used Also mixer but it too does not seem to help.

I can hardly hear anything if I have my volume less than 100% 

Any help on this would be great.

PS: I have a system capable of 5.1 but am using just stero. Any way to tell the system to pump everything into thse 2 speakers instead of expecting some other speakers to add the volume?

---

