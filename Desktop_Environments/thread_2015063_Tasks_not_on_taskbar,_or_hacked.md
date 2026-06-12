---
title: "Tasks not on taskbar, or hacked?"
date: 2012-07-02
forum: Desktop Environments
---

### Post by PcMojo on 2012-07-02
I've been having problems recently with the functionality of the taskbar. While researching it, I came across a post by etienoo, from just a few hours ago. The weird thing is that I am using Gnome and etienoo is using xfce. My problem is that the task bar stays empty. I have a task bar, but when I start a new application nothing appears on the taskbar showing that something is running. The day before the problem started, I installed Red Eclipse (which I have since uninstalled). The next morning my desktop changed upon startup; the wallpaper/background changed and my quick icons in the upper left were gone. Then I noticed problems with the taskbar. I thought I'd been hacked and looked at my firewall. It was off! Now everytime I reboot I have to turn the firewall back on. Sometimes Terminal command history isn't all there either. Have I been hacked?  Has anybody else experienced the “no tasks on taskbar” issue? I'm backing up all data expecting to reinstall (again :mad:), but would appreciate any opinions or possible fixes.

---

### Post by PcMojo on 2012-07-04
Update: I'm pretty sure I've been hacked. I've run RkHunter, Chkrootkit, and Tiger Tools and saw some suspicious activity. Startup files have been replaced, John the ripper downloaded, hidden files and hidden directories created, etc. I did a few virus scans and came up with about 40 items. My Gufw firewall is never on. Even after I turn it on, as soon as I check it again it is off. I have to open it, turn it on and leave the window open. So I don't think my taskbar issue is a desktop issue. I think it is a security issue so I can't see the programs the hacker is running. A moderator may want to move this post to the security threads. I'm going to reformat and reinstall Ubuntu for the 8th time in 6 months! Wow, even with my worst days with Windows Me, I didn't have to reinstall that many times. I will definitely be partitioning the hard drive as a duel boot. What's the old definition of insanity? Doing the same thing over and over and expecting a different result? </EndRant>

---

### Post by claracc on 2012-07-05
You don't give enough information:

What operating system are you running?
What are the hardware specs of your computer?
How do you know you have a virus?
What virus scan have you run?
What are the suspicious files addressed by rkhunter?
Have you installed software which is not in repositories?

I have been running  ubuntu dual boot with windows since year 2009 and never infected with any virus or trojan

---

### Post by PcMojo on 2012-07-05
Here are some things I noticed from running scans of RkHunter, ChkRootkit, and Tiger Security Scripts:

  	 	 	 	 	 	   From RkHunter:
 

 [20:41:48] Info: Found file '/usr/bin/groups': it is whitelisted for the 'script replacement' check.
 [20:41:49] Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
 [20:41:54]   /usr/bin/unhide.rb                              [ Warning ]
 [20:41:54] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
 [20:41:55] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
 [20:42:00] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
 [20:42:00] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check.
 [20:42:04] Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
 

 (several more tests were skipped or “disabled at users request”. I'm not sure why, I didn't ask it to skip or disable them. It could just be my unfamiliarity with the utility.)
 

 [20:42:58] Info: Test 'hidden_procs' disabled at users request.
 [20:42:58] Info: Test 'suspscan' disabled at users request.
 [20:42:58]   Checking for software intrusions                [ Skipped ]
 

 [20:43:04] Info: Unable to find the 'unhide-tcp' command
 

 [20:43:06]   Checking for hidden files and directories       [ Warning ]
 [20:43:06] Warning: Hidden directory found: /dev/.udev
 

 [20:43:06] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
 [20:43:11] Suspect files: 1
 [20:43:11] Applications checks...
 [20:43:11] All checks skipped
 

 

 

 

 ***** From chkrootkit
 

 Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:   
 

 /usr/lib/pymodules/python2.7/.path
 Checking `z2'...      user ___ deleted or never logged from lastlog!
 

 Checking `chkutmp'... The tty of the following user process(es) were not found  in /var/run/utmp !
 ! RUID          PID TTY    CMD
 ! root         1206 tty7   /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
 

 

 

 

 *****From Tiger security scripts *** 3.2.3, 2008.09.10.09.30 ***
 20:20> Checking permissions and ownership of system files...
 --CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'udev' is not recognised as a valid filesystem
 

 20:20> Checking for indications of break-in...
 --CONFIG-- [con010c] Filesystem 'devtmpfs' used by 'udev' is not recognised as a valid filesystem
 

 20:21> Performing system specific checks...
 /bin/grep: /etc/inittab: No such file or directory

---

### Post by PcMojo on 2012-07-05
To answer your other questions:
> What operating system are you running?
Ubuntu 12.04, Gnome 2 desktop
> What are the hardware specs of your computer?
[Dell D620]("http://www.dell.com/us/dfb/p/latitude-d620/pd#TechSpec")
> How do you know you have a virus?
I don't; I suspected being hacked (intrusion) and or trojans. While I am newer to Linux, I spent years disinfecting hundreds of Windows pc's. While at times I can be overly paranoid, I've also been able to detect suspicious activity when the best commercially available security software was saying that a PC was fine.
> What virus scan have you run?
Clam AV and Avast. Together they came up with about 40 items. Most of them I dismiss as overly sensitive heuristics, as many of the files I have had for years on multiple PC's without issue.
> Have you installed software which is not in repositories?
Not many. Usually only "semi-trusted" applications that you would see suggested on these forums. Things like RkHunter, Grub Customizer, etc. I've installed a few open source applications from Sourceforge, and commercial offerings like TeamViewer. The only thing I remember installing around the time of the problem was the game Red Eclipse from the Ubuntu Software Center. The next day is when the problems started.

There is nobody on my network but me and as I tried to post this to the forum, it just timed out. I tried another tab and Google timed out multiple times. That is not normal at all for my Internet connection. As I mentioned earlier, I have to open my firewall program and leave the window open for it to stay on. When I do, I'll get system errors every hour or so that my firewall program crashed and needs to be restarted. To me all this stuff just sounds like I'm under attack. Any help or advice would be appreciated. I've already backed up everything in case a reinstall is necessary.

---

