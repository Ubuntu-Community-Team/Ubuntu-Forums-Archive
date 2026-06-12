---
title: "Why i have to keep going back to windows :'("
date: 2006-02-27
forum: Desktop Environments
---

### Post by RTO on 2006-02-27
ok so i am a huge fan of linux and ubuntu, but always seem to find a reason to go back to windows. i keep my windows image on a partion so its handy but its abit to handy and i always seem to get frustraited with something and end up just reimaging the drive. i would really like to find solutions to the few problems i have with unbuntu. here they are.

oh and im using my trust acer 1350 notebook which runs it amazingly well.

1. ok so the biggest problem is with the power now speed steping. basically my notebook runs an mobile amd with powernow. which at full speed get way to hot for any notebook and the cooling system in this thing sounds like helicopter. so basically it does need to be steped down if you value your hearing... in windows i use a little program that steps my cpu all the way down to 318mhz which is fine for most things(steps up when i need it to). the problem is with ubuntu i cant (or dont know how to) get it to step down to that kind of speed. i use the emifreq-applet which works very well  but only steps it down to about 1.3 ghz which is alot faster than i need making it alot louder. so any help getting it to step down more would be great.
(cpu is a mobile amd 2600+)

2. i often transfer pics from my phone to my notebook via bluetooth. not found a way todo this in unbuntu yet. any ideas?  (i have a bluetooh usb stick)

3. there is also a slight sound issue that i have which i can only notice when using headphones. i hear a whitenoisey type sound even when there is no sound playing when its up past a certain lvl. sounds like something needs to be muted that isnt but ive tried all that and still have it. most people might not notice this but i do and it kinda bugs me might be a problem with the onboard sound support not sure. not a huge problem but would be nice to sort.

4. ok heres another biggy. i often use my notebook to things on my tv but cant for the life of me get tv out to work. is there a way to just get whatevers on the screen to be on the tv like windows? (gfx cars is ati radeon mob 9200 64mb an upgrade i did) 

5. amsn is great but i would prefer the normal one. is it possible to get it working with wine or anything like that? or is someone going to make a plugin for amsn so i can see what music my friends are listening too ;)

oh and i have a box setup as a file server (4 250gb drives raided together. works greats got years of data on) problem is its ofcourse an ntfs drive so cant right with notebook. 

currently im using a little work around i thought of. i made a small 10gb partition which is fat32 which i can write to on my notebook. most of the time im just reading anyway (media files) but for the odd time i need to save/change anything i either open it and save it to the fat32 partiton or save whatever there then i have a very simple batch file which runs every hour which just moves anything from the fat32 partation to the ntfs. which works well and does the trick just wondered if anyone knew a better way?

an help with these would be great and would help me ditch xp for good. 

p.s i dont want to dual boot (only a 30 gb hd and dont see the point in haveing 2 os's)

thanks

---

### Post by Mikecore on 2006-02-27
Try using the Ubuntu Wiki there are some tut's that could help you. I personally would not have re installed Win because of the things you have posted but I really really hate windows :). I sure most of the things you posted about can be fixed with a little searching and or time. Good luck and for get about windows.

---

### Post by RTO on 2006-02-27
well the speed stepping problem is what made me go back to windows.... so very loud... :|

---

### Post by RAOF on 2006-02-28
Can't help with anything else, but this:
[QUOTE=RTO]...
oh and i have a box setup as a file server (4 250gb drives raided together. works greats got years of data on) problem is its ofcourse an ntfs drive so cant right with notebook. ...[/QUOTE]
Your box is presumably sharing that array, over samba/windows file sharing, yes?  Then your Ubuntu box doesn't care that it's NTFS - it just asks the box to kindly read/write data for it.

For bluetooth you might want to try/wait for Dapper - that seems to load some bluetooth stuff on startup.  Don't know if it'd work for you, though :)

---

