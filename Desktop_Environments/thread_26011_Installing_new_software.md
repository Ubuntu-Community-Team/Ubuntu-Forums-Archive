---
title: "Installing new software"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Misagh on 2005-04-11
Hi folks, 
Firstly, I am really liking kubuntu so far. its the first linux distro i have stuck with for more than 2 days, (im currently testing out different distros, as this is my first time using linux, but have now settled for kubuntu).
I have just been learning how to install new software.
There were 3 pieces of software that I really wanted to install, firefox, gimp and bittornado.
I found out that I could go to 'Run Command' and type 'Kynaptic' which gave me a list of all the software I can install onto kubunto.

I managed to get the 3 software packages i wanted by going into root and typing :

sudo apt-get install mozilla-firefox
sudo apt-get install gimp
sudo apt-get install bittornado

Well, those 3 installed, however, I can only find firefox from the k-menu, its in the 'internet' section.
I can't find where it placed bittornado and gimp.
I would have thought that it would have put gimp into the 'Graphics' section, but its not in there, and I can't find bittornado.
So I went into the k-menu and went to 'Run command' and typed in 'gimp' and yay, it ran gimp. so I thought if I type in bittornado into the same place, it would run bittornado, but it just gives me an error that says : 'could not run the specified command'

So my question is, is there any way I can put gimp and bittornado into the k-menu so I can access them easilly.
also, I would have prefered to use azureus for my torrent downloading, rather than bittornado, but I could not find it in the kynaptic packages, does this mean that Azureus does not work with kubuntu?
Sorry, I am a total newbie, so I apologise if i have asked stupid questions that are obvious.
Thanks in advance for any help!

---

### Post by josel on 2005-04-11
I have Gimp in  K->Multimedia->Grapphics
You should have installed bittornado-gui also, i think. 
Bittornado Client is under K->Internet

I also dont have Azureus in the repos but you could download Java and Azureus i guess.
Take evt a look at [http://ubuntuforums.org/showthread.php?t=22860](http://ubuntuforums.org/showthread.php?t=22860) 

If you want to add programs to the k-menu just use kmenuedit to do it.

---

### Post by jobezone on 2005-04-11
If sometimes you can't find or remember a specific command or application name you want to execute in a terminal, or it just seems not to be working, although you know it is installed, open a terminal and write the first letters of the comand, then press [TAB] once or twice.
 This will complete the command(first [TAB]) and/or show the commands available to you which start with those letters(second [TAB]).
If this is confusing, just try it, and you'll understand!

---

