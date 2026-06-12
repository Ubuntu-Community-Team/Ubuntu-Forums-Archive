---
title: "Running a script as the user before shutdown or restart on Ubuntu 16.04"
date: 2017-03-08
forum: Desktop Environments
---

### Post by Yuval_Khalifa on 2017-03-08
Hi,

I have a Ubuntu Gnome desktop installed and on it I have installed VirtualBox. I would like to write a script that will automatically run before restart or shutdown to save the state of all the running VMs. 
I wrote the following script for that:
---------------------------------------------------------------------------------------------------------
#!/bin/bash


runningVms=$(sudo -H -u my_user VBoxManage list runningvms | sed ':a;N;$!ba;s/\n/;/g')
logger -s "$0[$$]: Currently running VMs: $runningVms"
sudo -H -u my_user VBoxManage list runningvms | while read -r vm_line; do
  vm_name=$(echo $vm_line | awk -F\" '{print $2}')
  vm_id=$(echo $vm_line | awk -F\{ '{print $2}' | awk -F\} '{print $1}')
  logger -s "$0[$$]: Saving state for $vm_name ($vm_id)..."
  sudo -H -u my_user VBoxManage controlvm $vm_id savestate
done
runningVms=$(sudo -H -u my_user VBoxManage list runningvms | sed ':a;N;$!ba;s/\n/;/g')
logger -s "$0[$$]: Currently running VMs: $runningVms"
--------------------------------------------------------------------------------------------------------

It runs perfectly well if I run it from the command line. I tried to create a script in the /etc/init.d that is exactly the same as this script and then to create symlinks to /etc/rc6.d/ and /etc/rc0.d/ and that didn't work (of course I chmod'd it to +x first) I didn't even see the lines that this script is supposed to write to the syslog (via logger -s). I tried to create a service in /etc/systemd/system that looks like this:

--------------------------------------------------------------------------------------------------------
[Unit]
Description=Auto save VMs state


[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/bin/true
ExecStop=/path/to/script_above


[Install]
WantedBy=multi-user.target
--------------------------------------------------------------------------------------------------------

and also this version of this solution:
--------------------------------------------------------------------------------------------------------
[Unit]
Description=Do something required
DefaultDependencies=no
Before=shutdown.target reboot.target halt.target


[Service]
Type=oneshot
ExecStart=/path/to/script_above


[Install]
WantedBy=halt.target reboot.target shutdown.target
--------------------------------------------------------------------------------------------------------


And this ran the script but it seems that all the services required for VirtualBox to run properly were already stopped so that the VBoxManage command failed.



The only way that I can think of making it work would be to rename the /sbin/reboot and /sbin/shutdown commands to something else and create my own files instead that will run my script and then call them.However, I have a bad feeling about it - Is that the ONLY thing that I can do? Is it the wise thing to do? Can it cause other problems that I don't know about yet?

Tnx,
Yuval.

---

### Post by TheFu on 2017-03-08
A few things about scripting.

a) always use full paths to all programs being run. - /usr/bin/logger is one. Do that for vboxmanage, su, awk, sed and all other non-built-in bash commands too. This is a best practice for scripting - especially since the PATH for end-users isn't the same as the PATH for root.
b) no need to use sudo when scripts already run as root - use **su** instead. Check the manpage for the exact option.
c) scripts don't have many environment variables - HOME isn't set, for example. Don't assume HOME. Don't know what that does to vbox commands, but since it is an end-user tool, not a system tool, it probably will have some issues.
d) 16.04 uses systemd to manage startup/shutdown processing. Using init.d/ scripts is old-school. Best to do it the systemd way. I haven't switched to 16.04 yet, so cannot help.

I've never used vbox on Linux. Check that the correct command is used. Case matters. Probably fine since it works from your login session.

Lastly, when posting code here, please, please used "code tags" so things line up and are easier to read.

---

### Post by Yuval_Khalifa on 2017-03-09
Hi,

Thanks a lot for all the info... You're, of course - correct... I forgot to use full paths and to replace sudo with su (I usually do remember that - this is just the first version of the script so I'll fix those), I don't think that I have assumed that $HOME is set.

As I have mentioned I have tested both the init.d and the systemd services options and the init.d script didn't really do anything (as far as I could tell from the logs) and the systemd service ran the VBoxManage tool but since all the other VirtualBox services were already off it failed. 

So as I've asked, the only way that I can think of making it work would be to rename the /sbin/reboot and /sbin/shutdown commands to something else and create my own files instead that will run my script and then call them. However, I have a bad feeling about it - Is that the ONLY thing that I can do in order to run my script as the FIRST thing the system does when asked to reboot/shutdown? Is it the wise thing to do? Can it cause other problems that I don't know about yet?

---

### Post by TheFu on 2017-03-09
> **Yuval_Khalifa said:**
>  
So as I've asked, the only way that I can think of making it work would be to rename the /sbin/reboot and /sbin/shutdown commands to something else and create my own files instead that will run my script and then call them. However, I have a bad feeling about it - Is that the ONLY thing that I can do in order to run my script as the FIRST thing the system does when asked to reboot/shutdown? Is it the wise thing to do? Can it cause other problems that I don't know about yet?

There are always repercussions for modifying stuff in this way. I wouldn't.
Your script needs to support "stop", "start", and "status" options in order to work.

And you actually don't want it to run "FIRST" - there are 50 other things that must work before Vbox can be run, at least.

Wise? No.

The system is designed to allow you to control startup and shutdown. There is at least 1 mistake, probably more, in the current attempt.

So ... 
* do the links have Snn-title and Knn-title names? (nn) needs to be a number, probably 00 to avoid issues.
* does the script support start/stop/status options?
* does the script have execute permissions?
* did you fix the su - so it switches to the useid you want?
* are you certain that vbox doesn't need HOME to run?
Please post proof of these things for help.  ls -l in all 3 init.d and rc? direcdtories and the full, updated, script would be needed.

---

### Post by Habitual on 2017-03-09
I have my dokuwiki.local installed in a Virtualbox-5.1 guest.
It runs headless and autostarts on my login to the desktop.
I reboot my host machine at will and my dokuwiki doesn't even notice.

What is the reasoning for your request, I guess I'm asking?

---

### Post by TheFu on 2017-03-09
Seems he doesn't want to reboot the systems for some reason. He wants to save/restore the VM state instead.  

I've never done this, but it would be fantastic if I were a software developer with my dev desktop setup _just so_ with multiple desktops having all my tools laid out perfectly.  For very large DBs or RAM-pinned DBs, might be nice too.

Or there could be 100 other reasons, right?
It is an interesting problem.

---

### Post by Yuval_Khalifa on 2017-03-09
> **TheFu said:**
> There are always repercussions for modifying stuff in this way. I wouldn't.
Your script needs to support "stop", "start", and "status" options in order to work.

And you actually don't want it to run "FIRST" - there are 50 other things that must work before Vbox can be run, at least.

Wise? No.

The system is designed to allow you to control startup and shutdown. There is at least 1 mistake, probably more, in the current attempt.

So ... 
* do the links have Snn-title and Knn-title names? (nn) needs to be a number, probably 00 to avoid issues.
* does the script support start/stop/status options?
* does the script have execute permissions?
* did you fix the su - so it switches to the useid you want?
* are you certain that vbox doesn't need HOME to run?
Please post proof of these things for help.  ls -l in all 3 init.d and rc? direcdtories and the full, updated, script would be needed.

Hi.

Thanks a lot for your reply. I'll give it a go and I'll let you know. If I understand correctly, the script in /etc/init.d should handle start, stop and status commands and then I should create symlinks to it in /etc/init6.d and /etc/init0.d and the link names should begin with S00-my_script-title and K00-myscript-title and that the script should of course have execute permissions and also I should replace the call for sudo with a call to su and maybe just in case - to set the HOME variable myself to the relevant folder.

The only thing that I don't know is what my init.d script should do with a 'start' command... the only thing that I want is to save the VMs state on SHUTDOWN which probably means that my script should be called on the stop command...

Thanks a lot,
Yuval

---

### Post by TheFu on 2017-03-09
You can't use S00-.... or K00.... the lower numbers are run first. That won't do. Your script needs to be run last.  Also, those directory names are wrong. I don't know if that will work on a systemd-based system. It may not. The script is the old init.d/ method. You'll need to test.

As for what to do with the start/stop/status .... look at the other scripts in the init.d/ directory. Use them as examples.

But you really should do this the systemd way. [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

