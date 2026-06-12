---
title: "Dell Ubuntu Problem"
date: 2008-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JSkills on 2008-06-08
Hey, I'm pretty dumb when it comes to computers and really don't know anything about fixing them when problems occur. I know a little, but very little. The problem I am having is I was running an old dell comp with ubuntu as the OS. My younger sister who is 6 uses it, and I believe she shut it down improperly. When I try to start up the comp it comes up with a message saying a file is corrupted and performs all these actions after saying that, the actions pretty much go no where, and it doesn't fix anything. I have the right to type in commands, but I don't know of any commands to type in. Also, there is no options in choosing anything, there is no "safe mode" or any options what so ever.

Another thing you might want to know about this comp is it doesn't have a cd drive. I didn't have a cd drive to spare, so for installing ubuntu I had to remove the cd drive from the pc I am using now, and temporarily use it on that comp in order to install the OS. Is there anyway I can fix the problem of the "file corruption" and get this comp to start up again? A simple command to type in would be nice.. but I have a bad feeling its not going to be that easy..:(. Can you guys help me some? It would be greatly appreciated.

---

### Post by tgrimley on 2008-06-09
Could you explain a little more about what you mean by there is no hard drive?  Where is Ubuntu booting from, etc?

---

### Post by JSkills on 2008-06-09
Yeah I'm sorry, I just recently figured out that a "hard drive" is not the same thing as a "cd drive". What I mean't to say was the comp doesn't have a cd drive. I guess I've got alot to learn about internal pc hardware :D. I'll edit that mistake now.

I talked to a person who taught me alot within the past 20mins and so Im going to post everything he suggested. This ubuntu comp was basiclly shut down improperly, and this caused a "file corruption" error, following this.. on the same page it tells me it needs to perform a whole bunch of actions, it performs these actions pretty quickly and they pretty much do nothing. It then leaves me with the option of restarting the computer "normally" with the hotkey it lists as "Control-n". I've tryed this, and it just does exactly that, it will restart comp normally, and basiclly the whole process of file corruption etc repeats itself. The other option I have after the actions are taken place with a fail, is entering commands. I am clueless on any commands what so ever, so that doesn't help me any. And thats all I am left to do, which leaves me stuck.

The guy I recently talked didn't know a great deal about Ubuntu, but what he suggested was in order to fix the "file corruption" problem, I need to find a cd drive for the comp. Connect the cd drive into the comp and put in the ubuntu OS cd. He wasn't sure if the comp would list a "boot from cd" option when doing this, and neither am I, although I hope it does. He said if I could get it to boot from cd there is a possibility the Ubuntu Os Cd would have a "repair installation" as does Windows. With my luck I feel it won't, but maybe I'll get lucky. Hope all this info helps. I going to have alot of problems trying to set up a cd drive into the comp, so I am hoping it doesn't require using a cd to fix the problem, do you think there is anyway of fixing it without using a cd? Like a simple command, etc?

Although if I remember correctly the error page mentions something about starting the comp in safe mode to fix the problem, now I don't know if you can run a "safe mode" on ubuntu, or what the command is to do so. I don't even know what to do if I got to the point where the safe mode was running, would the safe mode simply fix the problem all on its own, or will you have to do things when getting onto safe mode? I have a feeling this is going to be a real pain in the butt ;(.

---

### Post by talktoari on 2008-06-09
About the safe mode of Ubuntu,

While booting up, the options are provided for "recovery mode". That is itself the safe mode for ubuntu. This is mainly intended to actually limit but still provide major services to actually fix and correct errors / corrupted software installs, etc.

What file is it complaining as "File corrupted". Does it give the location as well?

---

### Post by GenesisV2.0 on 2008-07-02
Hi, now i am gonna approach this from a salvage angle ok so if your after someone to save your system then im not your guy but if you want your files and an ubuntu system that works then listen up.

your going to need to get where you can enter commands

1.grab a large memory stick or external hard drive

2.connect it to usb

3. create a folder "mkdir /media/saveme"

3. mount it  "sudo mount /dev/hda1 /media/saveme"  (instead of hda1 you can use something similar that your comp is doiung to refer to the usb device like hda2 hda3 usb1 usb2)

4 copy your hoem directory to the usb stick "cp ./"YOURUSERNAME" /media/saveme"

5 eject the memory stick "eject /dev/hda1" (or your memory stick abreviation

6 store those file son your other comp in a folder (forget about windows linux format problems aslong as there not changed)

7 install ubuntu on the memory stcik (you can download a free iso burner to do this)

8 boot of the memory stick and perform a clean install

9 refill the memory stick with your data after formating it and mount it again

10 fill your home directory again


there -- you will have your files and work but have lost prefernces and apps and such which is a kick in the teeth but its better than an unuseable computer  

sorry but thats would be my answer

hope i helped

---

