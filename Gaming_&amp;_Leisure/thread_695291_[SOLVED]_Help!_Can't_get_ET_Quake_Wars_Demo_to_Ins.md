---
title: "[SOLVED] Help! Can't get ET Quake Wars Demo to Instal..."
date: 2008-02-12
forum: Gaming &amp; Leisure
---

### Post by chazdraves on 2008-02-12
Firstly, I'm a Linux newb. Secondly, I already read through this thread: [http://ubuntuforums.org/showthread.php?t=600041](http://ubuntuforums.org/showthread.php?t=600041) which describes my exact same problem, but doesn't seem to resolve it.

I have the file on my desktop, I have set it as executable both in the GUI and in the Terminal. I have tried the sudo sh command and the ./filename command. Doing sudo sh gives me the Syntax unexpected "(' error and doing the ./ command gives me "No Directory or File" error.

I'd greatly appreciate some help. I'm rather stumped here...

Thanks, all!
- Chaz

---

### Post by Vadi on 2008-02-12
Can you please post the exact terminal output still?

---

### Post by chazdraves on 2008-02-13
Certainly. For reference, I renamed the file to ETQW.run to save on typing time...

chaz@chaz-desktop:~$ '/home/chaz/Desktop/ETQW.run' 
bash: /home/chaz/Desktop/ETQW.run: No such file or directory
chaz@chaz-desktop:~$ sudo sh '/home/chaz/Desktop/ETQW.run' 
[sudo] password for chaz:
/home/chaz/Desktop/ETQW.run: 1: Syntax error: "(" unexpected
chaz@chaz-desktop:~$ cd Desktop
chaz@chaz-desktop:~/Desktop$ sudo sh ETQW.run
ETQW.run: 1: Syntax error: "(" unexpected
chaz@chaz-desktop:~/Desktop$ ./ETQW
bash: ./ETQW: No such file or directory

- Chaz

---

### Post by tkmn on 2008-02-13
Some kind of shell issue, I don't know why bash also failed.

Use ./ETQW.run

Or you could just double click the file.. ;)

You don't **have** to use the terminal
[COLOR="Silver"]
*Actually, double clicking it only worked with the new demo,  ETQW-demo2-client-full.r1.x86.run and not the old 1.1 release.*[/COLOR]

---

### Post by chazdraves on 2008-02-13
I'm afraid double-clicking was the first thing I tried as a Windows user. That yielded nothing. If you look above, you'll see that ./ETQW.run returns "bash: ./ETQW: No such file or directory". Heck, even if I drag the file into the terminal and hit enter it still tells me the file doesn't exist... Thanks for the idea though.

- Chaz

---

### Post by Perfect Storm on 2008-02-13
```
cd ~/Desktop
chmod +x <file>
sudo ./<file>
```

---

### Post by chazdraves on 2008-02-13
Heh.

chaz@chaz-desktop:~/Desktop$ cd ~/Desktop
chaz@chaz-desktop:~/Desktop$ chmod +x ETQW.run
chaz@chaz-desktop:~/Desktop$ sudo ./ETQW.run
[sudo] password for chaz:
sudo: unable to execute ./ETQW.run: No such file or directory

I just don't understand this. I'm afraid this is why I've never switched fully over to Ubuntu. There just seem to be some things that are a lot more difficult than they should be. I'm beginning to wonder if it isn't still a programmer's OS and something I should shy away from.

Thanks for the idea, though.
- Chaz

---

### Post by Vadi on 2008-02-13
Not really, because I didn't come across this trouble when installing it.

Do "cd Desktop" and "ls", tell me what does it say? This is a bit weird.

---

### Post by chazdraves on 2008-02-13
Yes, I'm afraid I'm rather baffled. By this point in Windows I could have played it to death and already decided to uninstall it. :)

chaz@chaz-desktop:~$ cd Desktop
chaz@chaz-desktop:~/Desktop$ ls
ETQW-demo2-client-full.r1.x86.run  ETQW.run
chaz@chaz-desktop:~/Desktop$ 

It lists ETQW-demo2-client-full.r1.x86.run because I'm re-downloading it with BitTorrent in case something is buggered with the first one (ETQW.run), but I'd rather just get the first one working instead of waiting for another 700MB.

I really appreciate the help guys. Hopefully we can crack this.

- Chaz

---

### Post by Perfect Storm on 2008-02-13
```
cd ~/Desktop
chmod +x ETQW-demo2-client-full.r1.x86.run
sudo ./ETQW-demo2-client-full.r1.x86.run
```

Sounds like the other one is broken.

---

### Post by chazdraves on 2008-02-13
Such a thing... Well, I'm at 26% on the new download. I'll get back to you all in about "49 Minutes".

Thanks again,
- Chaz

---

### Post by chazdraves on 2008-02-13
Same song, different verse, I'm afraid.

chaz@chaz-desktop:~/Desktop$ chmod +x ETQW.run
chaz@chaz-desktop:~/Desktop$ sudo ./ETQW.run
[sudo] password for chaz:
sudo: unable to execute ./ETQW.run: No such file or directory
chaz@chaz-desktop:~/Desktop$ sudo sh ETQW.run
ETQW.run: 1: Syntax error: "(" unexpected
chaz@chaz-desktop:~/Desktop$ 

This is with the new file which I renamed to ETQW.run.

- Chaz

---

### Post by Perfect Storm on 2008-02-13
Have you tried not renaming it and see if it's the problem.
I know it sounds stupid....

---

### Post by Vadi on 2008-02-13
Where are you downloading it from?

And I just got the retail copy of the game, installing now :]

---

### Post by chazdraves on 2008-02-13
I think the first copy I got from SourceForge and the second one (which was 2.0 and the first was 1.1) came from some random Torrent I found linked through AI's Linux Games list.

I tried both of them without renaming before I renamed. Something's really buggered. The install of Ubuntu is only 2 days old, too...

I think I've decided that I'll be re-installing XP when I get back from errands. So, if anyone has any final ideas, let me know. Otherwise, it's probably just as well. Linux is a bit deep for even an advanced Windows user/computer geek such as myself. I've always done well at troubleshooting, but Linux doesn't allow you to just poke around menus until you figure it out. In Linux, you have to speak the language.

Dag... that'd make a great signature...
- Chaz

---

### Post by Vadi on 2008-02-13
Whatever - using classical excuses won't get you anywhere. Nobody will pity you here either - we aren't making money off new users, and if you're with the "Meh, I'm not impressed." attitude, then this isn't for you.

Btw, here's the official torrent for the demo: [http://zerowing.idsoftware.com:6969/torrents/f59b20f69f1cd2a7a6d9e0dd11d131ca5eaef344.torrent](http://zerowing.idsoftware.com:6969/torrents/f59b20f69f1cd2a7a6d9e0dd11d131ca5eaef344.torrent)

And lastly, if it doesn't work - feel free to contact the maker of this setup - because you don't blame a faulty program in Windows on Windows either.

[http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)

---

### Post by chazdraves on 2008-02-13
Wow... That kinda came from no where. My tone is not accusatory, I'm merely frustrated. Obviously, I'm impressed enough that I dared to make it my primary OS, but I'm just finding myself a bit discouraged as my Wi-Fi doesn't work, I can't get most anything I download (this is not the first instance) to work properly, I don't understand or have the time to learn all the console commands, and I frankly cannot seem to "get it".

I appreciate the help, all. Know that I haven't reformatted yet, but I do have the disc in hand.

Regards,
- Chaz

---

### Post by Vadi on 2008-02-13
As far as I see, you launch the installer okay - there's just an error in it, hence it complains :|

---

### Post by chazdraves on 2008-02-13
Well, I'm going to try the link you posted for the official torrent. I'm downloading it to a different folder, and I won't rename it at all this time... We'll see what happens.

- Chaz

---

### Post by chazdraves on 2008-02-13
More of the same, I'm afraid.

chaz@chaz-desktop:~$ chmod +x ETQW-demo2-client-full.r1.x86.run
chaz@chaz-desktop:~$ sudo ./ETQW-demo2-client-full.r1.x86.run
[sudo] password for chaz:
sudo: unable to execute ./ETQW-demo2-client-full.r1.x86.run: No such file or directory
chaz@chaz-desktop:~$ ETQW-demo2-client-full.r1.x86.run
bash: ETQW-demo2-client-full.r1.x86.run: command not found
chaz@chaz-desktop:~$ sh ETQW-demo2-client-full.r1.x86.run
ETQW-demo2-client-full.r1.x86.run: 1: Syntax error: "(" unexpected
chaz@chaz-desktop:~$ 

This is horribly bizarre...
- Chaz

---

### Post by Vadi on 2008-02-13
Are you on 64bit or 32bit ubuntu, do you know?

---

### Post by Vadi on 2008-02-13
You know I just realized - what I downloaded was the _original_ demo client. Then it updated itself.

While you're using the latest demo client that doesn't need updating - so maybe they broke it with the 1.4 update (it's quite recent).

Give me a moment, I'll find a link for the original one.

---

### Post by Vadi on 2008-02-13
Here you go: [http://www.mininova.org/tor/943208](http://www.mininova.org/tor/943208)

Download that one and try it. Just let it update before playing.

---

### Post by chazdraves on 2008-02-13
I'm using 64-bit. The first one I downloaded was the 1.1 client. It was only the last two that were 2.0 clients. I'll give it a try, but I'd expect the same. It seems like something simply isn't happening in the OS. I don't feel it's the file's fault, but then again, I'm am a total newb.

- Chaz

---

### Post by Vadi on 2008-02-13
If it's a shell script (like that is, I think), and it tries to access a file/folder that doesn't exist, the error will be printed out on the screen. So that's what I suspect is happening - the script -is- executed, but it's looking for something in the wrong place, and you get that error msg.

---

### Post by chazdraves on 2008-02-13
But it just seems so highly unlikely that all three of those downloads (from three seperate, trusted locations) are all bad... I mean, I see where you're coming from, but I still think it's something in Ubuntu. Is there anything anyone can think of that could be set wrong? Some library or something? I'm totally in the dark here. I'm tempted to pick up the retail version at Target, but I just figure I"ll have the same problem.

- Chaz

---

### Post by chazdraves on 2008-02-13
Well, I went out and purchased the retail copy only to find it's the same problem. Why the bloody heck can't I run .run files? As if that weren't enough, I just bought an iPod which I also cannot get to work... Is there something wrong with my install? If this really is Linux, I cannot imagine anyone using it, so there must be somthing buggered?

- Chaz

---

### Post by Vadi on 2008-02-13
Well yeah, since I'm playing retail now..

I'd say post in the Absolute Beginners forum for help, since nobody really does support that extensively in this section.

---

### Post by chazdraves on 2008-02-13
Allright. I got it! Not that I got it on my own, mind you, but I finally took the time to read AI's guide for installing QW on 64-bit: [http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

I think it was the first steps there that did it, because it worked immediately thereafter.

I still have to figure out the iPod (SoundConverter won't convert and GTKPod won't transfer), but I think I'm going to try Amarok for that.

Thanks everyone. It's a pretty fun game.
- Chaz

---

### Post by Vadi on 2008-02-14
Excellent :)

Click on "Thread Tools" on top and "Mark Thread as Solved" (it'll help when others are searching for the same solution)

---

