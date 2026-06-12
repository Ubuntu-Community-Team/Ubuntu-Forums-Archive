---
title: "Cannot install programs"
date: 2008-12-30
forum: General Help
---

### Post by bottosai88 on 2008-12-30
Hey i need a bit of help installing actual programs. Sometimes when i download stuff it downloads some gdi package installer which installs a package which i do not know what the ****. Um otherwise when i have a program to install like ad aware or avg or any program it likes make me choose or find an installer or some kinda installer which is used to install the program itself, Sorry i am having a hard time getting a pic but i mean does anyone just from reading have ANY idea, I just got a new ipod and want to be able to get itunes and frostwire which btw downloads as a gdi package installer. Any help would be really really appreciated.

---

### Post by taurus on 2008-12-30
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You don't need adware or avg for Linux.

---

### Post by exploder on 2008-12-30
Your question leaves me a bit confused but I will try to give you an answer. You need .deb files to install the packages you want. You can google for Limewire or Frostwire for ubuntu and you should be able to find deb packages for them.

You will have to use a Linux equivalent for Itunes because that is Apple software. There are plenty to choose from, Exail, Banshee, AmaroK and a whole bunch more.

Most packages can be found right in the default repos using Synaptic. A little bit of searching with google will help you choose what you want because you can check out screen shots and read other peoples comments.

---

### Post by bottosai88 on 2008-12-30
Thanks for the reply but this is partly helping but partly not. This PARTLY helps but is kinda confusing me, Any other help stuff cause i really am not taking this in, Maybe i am just a retard but its a bit confusing in terms. I want frostwire and iTunes at the moment but frostwire comes as a GDI Package installer. iTunes does not have a linux installer so i have no idea what to do with that.

---

### Post by SonnHalter on 2008-12-30
itunes does not support linux-yet. you'll have to download WINE. and then follow this guide-http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/


it's pretty easy to do. just keep going with it

---

### Post by bottosai88 on 2008-12-30
Ach as much as i like experimenting with new stuff, i am starting to hate this aspect of linux with a passion I guess i am gonna have to put up with it until i can find my reformatting discs, Thanks for the help guys i will try your stuff but linux was an experiment for me really, got a disk off a friend and am at the moment like said waiting for the ability to reformat. Chances though i will run a dual boot but i do not know if i feel like going through this crap constantly.

---

### Post by taurus on 2008-12-30
You can get frostwire from here, [http://www.frostwire.com/](http://www.frostwire.com/).  After you've saved it to your desktop, just double-click it to install it.  And before you can run it, you need to install sun java.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the java license screen, press the Tab key to highlight the <OK> and Return key to accept it.  

Now, you can run frostwire from Applications -> Internet.

---

### Post by exploder on 2008-12-30
Here is the Frostwire deb package you can install.

[http://www.getdeb.net/search.php?keywords=frostwire](http://www.getdeb.net/search.php?keywords=frostwire)

Download the package to your desktop and click on it to start the install.

Edit:taurus is correct about java, just follow the instructions he provided. Just copy and paste the commands.

---

### Post by luisito on 2008-12-30
You are very confused. Let me try to clarify a few things.

1. In order to install a program in Ubuntu you don't need to download anything from any website. You run a program called Synaptic (somewhere in your system menu) where you will find a (pretty huge) list of programs and you select the ones you want to install.

2. iTunes runs on Mac and Windows only. Not linux. On linux you have other music players. You can install rythmbox using Synaptic. Or you can also try xmms, which is pretty much like winamp. You may or may not like iTunes better. There are many music players on linux so you can experiment for a while.

3. Frostwire is also a windows program. On Ubuntu you can find a somewhat equivalent program by installing (using Synaptic of course) mldonkey-server and mldonkey-gui (or kmldonkey if you are using kde).

4. ad aware and avg are windows only programs to protect you from known spyware and viruses. There are no virus or spyware on linux, and thus no need to worry. That is the kind of crap that WE do not have to go through.

---

### Post by luisito on 2008-12-30
Errata: Actually you can install frostware using the instructions that the kind dudes posted above.

---

### Post by taurus on 2008-12-30
> **luisito said:**
> You are very confused. Let me try to clarify a few things.

1. In order to install a program in Ubuntu you don't need to download anything from any website. You run a program called Synaptic (somewhere in your system menu) where you will find a (pretty huge) list of programs and you select the ones you want to install.

2. iTunes runs on Mac and Windows only. Not linux. On linux you have other music players. You can install rythmbox using Synaptic. Or you can also try xmms, which is pretty much like winamp. You may or may not like iTunes better. There are many music players on linux so you can experiment for a while.

3. Frostwire is also a windows program. On Ubuntu you can find a somewhat equivalent program by installing (using Synaptic of course) mldonkey-server and mldonkey-gui (or kmldonkey if you are using kde).

4. ad aware and avg are windows only programs to protect you from known spyware and viruses. There are no virus or spyware on linux, and thus no need to worry. That is the kind of crap that WE do not have to go through.

1.  Not every program is available in add/remove or synaptic.

3.  Frostwire is not just a windows program.  There is version for Ubuntu (Linux).

---

### Post by bottosai88 on 2008-12-30
Yea i am getting what you are saying but at the same time its confusing the crap out of me i found that frostwire in synaptic but idk this is just getting annoying having to do all of this, Thanks again for the help but i may just wait til i can find my reformat discs and floppys. Thanks everyone for the help any more info go ahead hit me with it i will keep checking this thread and trying little by little to utilize what is in this post.

---

### Post by exploder on 2008-12-30
bottosai88, installing packages gets easier and easier after a couple of times of doing it and there are thousands of applications to choose from in the default repositories using Synaptic. Give it a shot, what do you have to loose?

---

### Post by bottosai88 on 2008-12-30
True..... Thanks man i guess ima get on crackin this stuff.

---

### Post by bottosai88 on 2008-12-30
Btw which one of these am i?

Then, copy and paste one of the lines below depending on which version you are running.

For Ubuntu Intrepid (8.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

For Ubuntu Hardy (8.04):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

For Debian Etch (4.0):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) etch main #WineHQ - Debian 4.0 "Etch"

---

### Post by TestDummy! on 2008-12-30
Assuming you downloaded the most recent version, it's the first.

---

### Post by bottosai88 on 2008-12-30
And how do i download this Richies text crap, Its in text do i copy and save the text or what? This is confusing but helps me kill a bit o time, btw i am installing this wine and am ojn this software sources. Anyone got any real real easy instructions that may help cause i need to get this done asap

---

### Post by TestDummy! on 2008-12-30
I don't understand what you're asking.

---

### Post by bottosai88 on 2008-12-30
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)  I am trying to do that so i can get itunes.

---

### Post by TestDummy! on 2008-12-30
You save the key to your desktop, and then import it into Synaptic. Try right-clicking and "Save link as".

---

### Post by ByKeLaO on 2008-12-30
EDIT: Disregard this message, I forgot to refresh the page and it seems the question has already been answered :P

---

### Post by bottosai88 on 2008-12-30
BUT I CANNOT SAVE IT. It opens it as a page of text, NO SAVE or DOWNLOAD options.

---

### Post by TestDummy! on 2008-12-30
You can't just right click the link that leads to the text?

---

### Post by bottosai88 on 2008-12-30
[http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/](http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/) ok now i am trying this part of the itunes installation. I am at that first part of the list, with that line of command

# Install deb package:
sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb

Is that a terminal command? I tried it in the terminal and it didnt do crap and if it is an install then there is no link to it.

---

### Post by bottosai88 on 2008-12-30
I also cannot figure out frostwire also, I went into synaptic and searched it but i cannot do anything to it or open the program. help with that would be appreciated also.

---

### Post by TestDummy! on 2008-12-30
Yes, it is a terminal command, but it won't work if you point it to a DEB that doesn't exist.

---

### Post by bottosai88 on 2008-12-30
alright disregard the one about frostwire i believe i got that part all i need help with is itunes. Thanks very much to anybody that has helped me

---

### Post by TestDummy! on 2008-12-30
Are you still unable to add the key from the "Download and save Scott Ritchie's key" if you right-click and save it (not left-click), and then import it into Synaptic as it says?

Even if you left click it and let the full text load, nothing really stops you from doing a File > Save Page As.
It's just text with a .GPG extension on it instead of .TXT

---

### Post by bottosai88 on 2008-12-31
yea its showing it where the pic is saying it should i just need the part from the iTunes which even though its runnin through all this crap and bypassing a lot will it harm my iPod at all cause it was expensive to buy or will it still put the songs on it fine.

---

### Post by TestDummy! on 2008-12-31
It's still hard to understand what you're asking.
Could you please clarify?

---

### Post by bottosai88 on 2008-12-31
Yea i think i may just wait for the ability to reformat cause i do not think i wanna spend this much time just to get this little done. Plus i do not want to screw up my ipod

---

### Post by bottosai88 on 2008-12-31
btw what i was asking was in this install iTunes page 

Install deb package:
sudo dpkg -i wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb

I want to do this but like i said i do not think i have this much time to just install one program. I am too new to linux. Plus like i said i do not want my iPod to get messed up.

---

### Post by bottosai88 on 2008-12-31
Yea if anybody knows if it will harm an ipod this method of getting iTunes can they please inform me cause i am doing this off a whim. If there is no harm that can be done to my iPod using this method then can someone please help me learn this method. By the way void those last messages of mine, just irritation talkin in those.

---

