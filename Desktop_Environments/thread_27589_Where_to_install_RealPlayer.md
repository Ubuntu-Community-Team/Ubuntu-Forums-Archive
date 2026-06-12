---
title: "Where to install RealPlayer?"
date: 2005-04-16
forum: Desktop Environments
---

### Post by lmellen on 2005-04-16
Could use some quick info. I want to try to download RealPlayer. When I start  apt-get the download wizard asks where I want to put the download?  I'm thinking /usr/bin??
 Does anybody know what  the correct directory is?
 I need realplayer because nothing else seems to work! Somebody suggested some servers are rejecting anything thats not actually realplayer. All I need is realplayer 7 or better.
                                                                                                    Thanks -- Larry  :smile:

---

### Post by crane on 2005-04-16
I would put Realplayer in eather /usr/share or /opt

---

### Post by bored2k on 2005-04-16
It doesn't really matter where. It will be installed with links for firefox pointing to the right direction. People's choise is usually /opt/ but I have it in ~/Files/RP

---

### Post by lmellen on 2005-04-17
I have realplayer installed and working. I might reinstall it -- one last question and I'm done with set up.
The installer supplied with the OS is useless, RealPlayer comes with it's own. 
I installed RealPlayer 10Gold. During install it asks:
                        "Configure system wide symbolic link Y/N" 
I type Y then it asks:
                        "Enter the prefix for symbolic links[/usr]:
What am I supposed to type in? I don't have a clue!
Why[/usr] I put it in /opt?
                                             Thanks for the replies --Larry :)

---

### Post by bored2k on 2005-04-17
[QUOTE=lmellen]I have realplayer installed and working. I might reinstall it -- one last question and I'm done with set up.
The installer supplied with the OS is useless, RealPlayer comes with it's own. 
I installed RealPlayer 10Gold. During install it asks:
                        "Configure system wide symbolic link Y/N" 
I type Y then it asks:
                        "Enter the prefix for symbolic links[/usr]:
What am I supposed to type in? I don't have a clue!
Why[/usr] I put it in /opt?
                                             Thanks for the replies --Larry :)[/QUOTE]
 Just hit enter everytime you get asked for something.

BTW, what installer supplied by the OS? I didnt know ubuntu came with RealP.

---

### Post by lmellen on 2005-04-17
[QUOTE=bored2k]Just hit enter everytime you get asked for something.

BTW, what installer supplied by the OS? I didnt know ubuntu came with RealP.[/QUOTE]
 
BTW, what installer supplied by the OS? I didnt know ubuntu came with RealP.

---

### Post by lmellen on 2005-04-17
When I first tried to " sudo apt-get install realplayer" a pop up window told me it was the installer. It gave me this address "http://scopes.real.com/real/player/unix/unix.html.
It told me to look for "Linux2.x(libc6i386)rpm" I was supposed to save the file in a directory of my choice and name the file "rp8-linux20_libc6_i386_cs2_rpm) -- (I'm not sure if I copied correctly.) It would then install when I sudo apt-get install realplayer,I guess.
 Problem was I couldn't find the required player, I couldn't download anywhere but to /home/lmellen -- (access denied - permission problem)-I had to sudo mv to get it to /opt.
So screw it, I've installed this player before, I did and it worked.I just didn't know what the symboloic link meant.
 I tried to go back to the installer, but real player is installed,so the installer window won't pop up again.
What's annoying me now is all the downloads go to Firefox, not Konqueror.( I 'm running Kubuntu).I'll worry about that later.
                                                Thanks for the replies -- Larry :)

---

