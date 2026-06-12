---
title: "New to Linux- questions!"
date: 2009-04-01
forum: General Help
---

### Post by wrose51106 on 2009-04-01
I decided to make the plunge over to Linux, got it installed but I have ran into a few issues. 8.10, I386, up to date.

I custom built the following machine:

ZOTAC nForce 630i-ITX 
Dual core Celeron 2 ghz
2 X 1 DDR2 800

Now I have questions!

1) Only displays 1 CPU, rebooting a few times it finally came up with 2nd but then it disappeared. It is enabled in the BIOS.

2) Opening a terminal, I type in "dir" and I can see my videos, pictures, desktop etc. folders, but when I "cd" into one of them it says it does not exist??? But I can "cd" out and navigate the filesystem just fine.

3) Opening a terminal, "ifconfig ethX up/down" it doesnt matter which, it says I do not have permission. The ethernet port worked great last night, now it shows it not even connected to my switch but the nic's lights are on. I need to grep it, gotta find that command....

4) Nvidia drivers installed, max desktop effects enabled. Opening Firefox, top left of the screen displays desktop/old Firefox info for about 1-2 seconds. Just annoying on that one.

5) Since Linux does not have a device manager, how can I tell if something is not functioning / or has a correct driver installed?

I got to say, I am very impressed. Can not wait to keep using this machine. So fast, smooth and stable! Only used Linux for a few hours so far but the commands etc remind me of DOS with the raw power of a heck of a gui.

-Bill

---

### Post by hyper_ch on 2009-04-01
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by bruce2000 on 2009-04-01
Hi and welcome to the forums :)

I can't help with most of your questions but will make a suggestion for #2

Are you sure you're typing the folder names with sensitivity to case? ie it is 'Videos' 'Music' etc with capital letters. (Unlike the old microsoft dos, Linux is case-sensitive.)

---

### Post by bruce2000 on 2009-04-01
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

The original poster has 5 questions - how can he mention all that in a subject line?

---

### Post by wrose51106 on 2009-04-01
Ya the OP is an idiot. Oh wait:)

Thanks for the welcomes and next time I will be sure to make multiple posts. Some places don't care for that, I plead ignorance!

On the question for #2 I will try the case sensative aproach. I have noticed this in the terminal but CD, I didn't think it would matter.

Any help on the others would be great, I am having a hard time understanding why it was picking up my NIC as eth5 though. What are the first 5 and why can't I access them. Got to say, absolutley loving this.

-Bill

---

### Post by 2genes on 2009-04-01
hey bill
welcome to ubuntu mania
i m a newcomer too, i installed ubuntu one week ago and till now im excited too.
that much , that i deleted the windows partion some minutes ago
Linux seems a little bit hard in the begining but as time goes on everithing becomes a peace of cake and this forum is really helpfull
so... welcome again and have fun

---

### Post by nebileix on 2009-04-01
Here's the command to find out what hardware has been detected.

```
$ sudo lshw
```

---

### Post by eeperson on 2009-04-01
1. How are you viewing your CPUs?  I am not entirely sure how Linux represents dual core processors as they are technically 1 CPU with two cores.

2. As mentioned by bruce2000 Linux is case sensitive, so make sure you are typing the names of the folders with the appropriate case.  Also, beware that the character '/' represents the root directory so if you type:

```
/Pictures
```

It is the equivalent of the windows:

```
C:\Pictures
```

In Linux the equivalent of 'dir' is 'ls'(think of it as the word 'list' shortened).  'dir' is sometimes provided (but not always) for people who are used to DOS.  If you want to learn about a particular command(such as 'grep') you can use the 'man'(short for manual) command just type:

```
man grep
```

Then a page describing how to use 'grep' will come up.  Press 'q' when you want to exit.

3. I am not sure about the specifics of your ethernet problem so I cannot address that.  However, I do know why you are getting the access denied error.  The reason for this is that Linux has a separate administrator user (known as the 'root' user) that can perform important administrative tasks like installing software or changing import system settings (like you are trying to do with that command).  Regular users cannot perform these tasks.  This is for security reasons and also to prevent a user from accidently doing something they shouldn't.  Fortunately, Linux provides a command that allows you to run a specific command with the privileges of the root user.  Just type the command 'sudo'(it is short for 'super-user do') in front of the command you want to run as root. So in your case something like:

```
sudo ifconfig eth0 up
```

You will then be prompted for your password.

4. This is probably due to a the version of the nVidia driver you have installed.  You can install a newer driver(it might fix it) but if it isn't bothering you too much it is probably not worth it.  Firefox is an application that that I find tends to have some rendering issues on launch.

5. Linux tends to come with nearly all of the drivers that exist for it(nVidia drivers are the most notable exception).  This means that you rarely have to go hunting down Linux drivers.  As a result of this there isn't really a device manager in the same sense as in windows because it isn't as needed.  However, there are graphical programs that will show you what hardware you have on your computer(this can already be checked through the command line with the command 'lshw').  They just aren't installed by default because there isn't enough room on an install CD.  You can probably find one by looking though the repositories (if you don't know what I mean by repositories, look it up, it is one of the best parts of Linux).

---

### Post by stereomuffin on 2009-04-01
For what its worth (i'm a beginner myself, so excuse me if i write nonsense)

1) cat /proc/cpuinfo | grep cores | uniq
to view the amount of cores detected? 

2) start using ls, you might also try ./ infront of your command.. so in your home directory try: cd ./Documents
in case cd Documents doesn't give any result from your home directory

---

### Post by wrose51106 on 2009-04-01
Thank you all for the help.

I ran cat /proc/cpuinfo and It listed the CPU as single core. I am going to play in the BIOS tonight, it *was* working earlier, perhaps my Wild Turkey last night did something....

I left the switch unplugged this AM and over my lunch hour went home and now it is working just fine, go figure. I ran lspci and noticed that it was infact an Nvidia nic. All is good on that front.

Now my biggest wonder is why the nic is showing as eth6 now :confused:

-Bill

---

### Post by aeiah on 2009-04-01
you can also check your cores using the system manager as well (menu > system > administrator > system manager)

i dont know what your eth0 - 4 could be, but if you do ifconfig in the terminal it'll give you a rundown of your network devices. lo is your local loopback. eth5 is your ethernet by the sounds of things.. maybe it'll tell you what the hell the others are :p

as for the changing directory thing not working, that's a bit strange. remember that pressing tab will autocomplete things for you in the terminal. it helps you avoid typos. another possibility is that you're typing

```

cd /Videos

```

the slash denotes the root directory, whereas Videos is probably at /home/username/Videos (can be abbreviated to ~/Videos). you dont need to specify the /home/username/ bit though because the terminal already starts in home.. but its worth bearing in mind that a slash before the foldername will make a difference.

```

cd Videos

```
so should work

---

### Post by Vaphell on 2009-04-01
few hints
~ is equivalent of your home directory, so no matter where you are in dir tree you can use cd ~ and you are back to /home/yourname/

also you can use tab key, it autocompletes names for you - killer feature
if you have Documents dir and you enter
'cd d[tab]'
it won't do anything, because of the case sensitive names (there is no match), but when you do 'cd D[tab]' it will add whole name but only if there is exactly 1 matching name. In case of many names starting similarly (like Documents and Doctor) it will stop at 'cd Doc' and will wait for further letter to conclusively decide which one you wanted (hitting tab twice shows list of all matching objects - very useful). This feature seriously speeds things up when using terminal.
Autocompletion works not only with paths but also in case of commands, you can enter 'nau[tab]' to get nautilus.

---

### Post by Tews on 2009-04-01
> **bruce2000 said:**
> The original poster has 5 questions - how can he mention all that in a subject line?

HyperCH likes to paste that into all posts that dont live up to what he thinks a proper request for help.  This does nothing to help and gets really annoying after seeing it over and over.

---

### Post by stereomuffin on 2009-04-01
> **Vaphell said:**
> 
also you can use tab key, it autocompletes names for you - killer feature


Indeed, also try history or CTRL-R to search threw your bash history.. so in case you forgot some kind of important command you can do: history | grep partofcommand and it will list it

So lets say you forgot the command to restart your apache webserver
you could issue something like:

history | grep apache

It would output something like:

```
 

me@mybox:~$ history | grep apache
   
   40  sudo /etc/init.d/apache2 start
   44  sudo /etc/init.d/apache2 stop
  104  sudo nano -w /etc/apache2/httpd.conf
  106  sudo nano -w /etc/apache2/httpd.conf
  107  locate apache
  109  locate apache2.conf
  110  /etc/apache2/apache2.conf
  111  sudo nano /etc/apache2/apache2.conf
  510  history | grep apache


```

The number infront of the line you can now use to issue the command again, so say you want this command: sudo /etc/init.d/apache2 start

You would then simply type: !40
and the shell will run it.. Pretty cool stuff :p

---

### Post by wrose51106 on 2009-04-01
Ok guys we are rocking out now.

1) Reset BIOS, SMP good to go.

2) Learned first hand,lower case is my "cd" friend.

I will keep posting, I am loving this OS. 10+ years teching on MS products, this Linux is something of a beast coming back from having everything done for you, and I am loving every minute of it.

-Bill

---

### Post by wrose51106 on 2009-04-01
Here is a copy of ifconfig:

william@william-desktop:~$ ifconfig
eth7      Link encap:Ethernet  HWaddr 00:00:6c:7f:4c:3b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe7f:4c3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10273930 (10.2 MB)  TX bytes:852042 (852.0 KB)
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8456 (8.4 KB)  TX bytes:8456 (8.4 KB)

william@william-desktop:~$

---

