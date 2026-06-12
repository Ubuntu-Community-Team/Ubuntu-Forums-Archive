---
title: "XAMPP on Desktop edition"
date: 2009-07-20
forum: Desktop Environments
---

### Post by taha116 on 2009-07-20
So i want to use Xampp on ubuntu desktop edtion but since im a nub (I know about server addition but i cant use that so dont waste your time)I cant figure out what shell login is?

"Go to a Linux shell and login as the system administrator root:"

Its part of their instilation instructions and i tried it with the admin account that i have... but i didnt do any special log in... turned on my computer.... logged into my account... tried it out... everytime i do this:

```
**[IMG]http://www.apachefriends.org/img/afbullet.gif[/IMG] Step 2: Installation**

After downloading simply type in the following commands: 

[LIST=1]
[*]Go to a Linux shell and login as the system administrator root: su
 
[*]Extract the downloaded archive file to /opt: tar xvfz xampp-linux-1.7.1.tar.gz -C /opt
 **Warning:** Please use only this command to install XAMPP. DON'T use any Microsoft Windows tools to extract the archive, it won't work.
 **Warning 2:** already installed XAMPP versions get overwritten by this command.
 
[/LIST]
  That's all. XAMPP is now installed below the /opt/lampp directory.
```

I get a authencation failed message after typing Su... and then my pasword...

Wats wrong? What am i suposed to be doing? I am guessing i am suposed to login first using a different method?

Thanks for the help!

---

### Post by quixote on 2009-07-22
You're, uh, kind of jumping in at the deep end if you want to install XAMPP, but those instructions don't make sense to you.  They're actually pretty basic, and if that's problematic, you may really want to get some more background first before you tackle this.

The "recipe" I followed to install server software on my desktop is [here]("http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06"). (Same procedure for intrepid or jaunty. The version numbers on some software may be higher, but I don't think so.)  That's LAMP not XAMPP.  I don't know whether that makes a difference for you.  The main thing as far as I'm concerned is that it works.  It also uses graphical interface, mostly point and click, and is nice and easy. :)

If you really want to follow the directions you quoted, then what that means is:  "Linux shell" = command line.  Open a terminal (Start > Accessories > Terminal).  

Ubuntu doesn't use "su."  Su stands for "superuser" ie root, or Administrator in windows-speak.  Ubuntu uses sudo to run commands as root.  Every command that has to be run as root needs to have sudo at the beginning.  Running commands as root allows you to completely brick your system if you don't know what you're doing or you make a mistake.  

If you have a lot of commands to run as root, you can use "sudo -i" for sudo interactive, and then you get the straight root prompt.  The root prompt is generally shown as "#" whereas the user prompt is "$".  Running commands from the root prompt, you can **really** brick your system. I really really wouldn't advise it.

Good luck, and I hope you get your server running, one way or the other.

---

### Post by Viva on 2009-07-22
Try this:

[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

You'll have to change the file name to the latest one while extracting.

---

### Post by taha116 on 2009-07-22
Thank you very much! both of you.

I managed to install XAMPP completely and patch up all the security holes. I even got myself Webmin. Now ive gota setup the right paths and i should be set.

I am having some trouble still. **Two main issues**

1. How do i check my internal IP

2. local host give me a failed to connect error. Yesterday it didnt do that.... I dont understand the issue....  at all.... ppl saying it could be firewall or apache settings. My Router firewall cant be doing it.. im preaty sure its disabled... and i have firestarter on my computer... ill try to see what hapens if i stop it completley... ill get back to u ASAP if you have any ideas as to what i should to to maintain a secure server please let me know. (!---**Important **[I can acses webmin using [http://localhost:webminport](http://localhost:webminport) wich is odd so i think it not the firewall but something else... any ideas guys?] ---!)

---

### Post by taha116 on 2009-07-22
Ok so ignore the last post now...

I still need to find out what my **internal IP** is and ive managed to solve my xampp problem...

**I have installed a test copy of wordpress onto my new server.**
My major problem at the moment is that i dont know how to enable mail, because if som1 registers they will not get any mail. I tested myself.

Firstly i want to make sure PHP mail is enabled so if you would be so kind as to give me instructions like :
[I]
Find lines: example line -to- example line

Replace with example: example line -to- example line

[/I]For the php.ini fil[I]e.

[/I]Its important to note that my router has a firewall (its disabled) but i have a firewall called Firestarter amd have allowed http smtp and ftp inbound. You probably still cant access my test server but i can. This is because i havent forwarded ports from my router yet. Could this be a possible reason as to why it wont work as well? I do strongly doubt it but im no expert.

Thanks for the awesome council!
~Taha

---

### Post by quixote on 2009-07-22
Your machine's local IP may vary if your router uses DHCP.  In that case can you use the machine's hostname?  Log on to your router to find whether IPs are assigned statically or dynamically, and if the former, what the numbers are.

Congratulations on getting wordpress running!  Always a nice feeling.

I don't know anything about the email issue.  Remember that if you want to use this server as more than a test server, i.e. visible to the web, get email on it, and the like, then security is a big issue.  I've never done that, but the Ubuntu wiki does have a (long!) list of instructions on how.

---

### Post by taha116 on 2009-07-26
Thanks for the info im gona drop by the wiki more often.... 1 more problem though... everything works but i cannot find a good ISP with a fast uplink for the server. Any ideas or suggestions?

---

### Post by quixote on 2009-07-26
Where are you located?  One of the best resources I've found for comparison shopping all things internet is dslreports.com .  All those server adventures are going to be small potatoes, compared to finding a reasonable ISP if you're in the good old "we never met a monopoly we don't support" U. S. of A.  Good luck!

---

