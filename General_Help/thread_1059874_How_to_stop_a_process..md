---
title: "How to stop a process."
date: 2009-02-04
forum: General Help
---

### Post by lazman on 2009-02-04
I was trying to get vnc viewer to work in listen mode. I found this [post]("http://ubuntuforums.org/showpost.php?p=5064825&postcount=105") and it worked great. I decided to make a sh file and put it on the desktop for quick running of the server. I put the command line on that post in there and made it executable. I ran it then tested to be sure it was working, it worked great. However, I now have the process xtightvncviewer running in Zombie status according to System Monitor. I have tried to do stop process, end process, and kill process. None of these are working to shut it down.

Is there another way to shut it down? And perhaps a better way to run it from the file to have the option to shut it down from command line? There was not terminal window opened when I ran it.

Thanks!

---

### Post by blazemore on 2009-02-04
hit alt+f2
type xkill and hit enter
click the window you want to close

---

### Post by lazman on 2009-02-04
Wow I just learned something useful! However, there is no window to close with this process.

I just found this [page]("http://pwet.fr/man/linux/commandes/xtightvncviewer") but I see no command to stop it.

---

### Post by Neural oD on 2009-02-04
type sudo su
then type kill -9 xxxx  - where xxxx is the process number
then type exit

---

### Post by Neural oD on 2009-02-04
or you could type sudo pkill xxxx 
where xxxx is the process name

---

### Post by lazman on 2009-02-04
This is very useful information! I just did figure out how to stop it using the System Monitor. What I done was checked show dependencies in the view menu. After I done that it displayed a process of the same name that was not running as zombie on top of the zombie. I done kill process on that one and they both went away. 

It would be nice to have a better way to stopping it rather than kill process. I have my doubts because I see on the man page there is no command option to stop it once it's started. And no way to know ahead of time what the process ID will be to use the command line option you provided. When running the viewer in windows there is an icon in the system tray that can be used to close the viewer. I did not see such a thing on Ubuntu, so perhaps this IS the prefered way to close this application?

Thanks for all your help!


Ahh! I see you gave up ways to kill a process by number and name! Perhaps I could use the process name to automate closing it by sending the pkill command!

---

### Post by lazman on 2009-02-04
Ok wait! I'm making this much much harder than it has to be. All I have to do is click run in terminal instead of just Run when I click on the sh file on the desktop. When I close the terminal window the process is stopped and removed by Ubuntu! 

As a side note, this feeling of being a total nubie on a computer is starting to bother me. I can make windows run a 5k marathon, jump through hoops of fire, take the dog for a walk, and fix breakfast just in time for my morning yawn. But, now it's like starting all over again. It's rather frustrating to be honest. However, I am going to stay the course, because one day I will be able to make Ubuntu do nice tricks too! I guess at one time or another we were all where I'm at. I just wish I had fully taken the plunge long ago and learned both at the same time.

Thank you are all your help!

---

### Post by blazemore on 2009-02-04
That's one of the main problems with Linux adoption.

(not you personally)

It's not the beginners that are the problem. It's the Windows Power Users.
They think, because they know Windows inside out, that they "know computers".

Then they install Linux cos they think they're hard enough....
They soon find out that when something goes wrong they don't have a clue! But we're here to help you, and I personally try to explain each step so people learn, rather than just getting people to copy & paste commands.

---

### Post by eumetaxas on 2010-12-22
> **Neural oD said:**
> type sudo su
then type kill -9 xxxx  - where xxxx is the process number
then type exit

thank you!

---

