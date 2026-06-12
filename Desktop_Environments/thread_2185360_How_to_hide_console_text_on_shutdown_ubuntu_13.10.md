---
title: "How to hide console text on shutdown ubuntu 13.10"
date: 2013-11-02
forum: Desktop Environments
---

### Post by mal_skelton on 2013-11-02
[SIZE=3]H[FONT=arial]ello[/FONT]
     [FONT=Arial]I've been using Ubuntu for a while but I'm no expert. I recently upgraded to Ubuntu 13.10 from 13.04 on my [/FONT][FONT=Arial]dual boot [/FONT][FONT=Arial]win 7 Desktop [/FONT][FONT=Arial](x86_64 bit) [/FONT][FONT=Arial]running on an [/FONT][COLOR=#000000][FONT=Arial]Asus P8Z77-V DELUXE mbo with Intel i5-3570K 3.40GHz (Ivybridge) Graphics. Ubuntu and Windows are on a  partitioned [/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Arial]Samsung[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#000000][FONT=Arial] SSD[/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][COLOR=#00000a][FONT=Arial] and I have an [/FONT][/COLOR][/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#ffffff][FONT=SimSun][COLOR=#00000a][FONT=Arial]ASUS VH242H 24" 1920x1080 resolution[/FONT][/COLOR][/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#ffffff][FONT=SimSun][COLOR=#00000a][FONT=Arial] monitor. Kernel 3.11.0-12-generic is installed and generally everything is working fine. After upgrading, I'm now getting a brief splash of text appearin[/FONT][/COLOR][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][COLOR=#00000a][FONT=Arial]g just before the white dots when rebooting or shutting down the computer. Is anyone able to explain what these messages mean? Is there anything wrong? Is there anything I can do to hide or to stop these messages [/FONT][/COLOR][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][COLOR=#00000a][FONT=Arial](see below) from appearing during reboot or shutdown? [/FONT][/COLOR][/FONT][/COLOR] [/SIZE]

      [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Ubuntu 13.10 buntu ttyl[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]sid@[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]buntu:~$ sudo halt[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
  

  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Broadcast message from [/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]sid[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]@buntu (/dev/ttyl) at 19:41 ...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]The system is going down for halt NOW![/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]sid[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]@buntu:~$ acpid: exiting[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Stopping web server apache2[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*] 
[/LIST]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]speech-dispatcher disabled; edit /etc/default/speech-dispatcher[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Stopping NFS kernel daemon[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Unexporting directories for NFS kernel daemon...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Asking all remaining processes to terminate...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]All processes ended within 1 seconds...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[/LIST]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]rpcbind: rpcbind terminating on signal. Restart with “rpcbind -w”[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Unmounting temporary filesystems...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Deactivating swap...[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Unmounting local filesystems... [/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[/LIST]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]mount: / is busy[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
 
[LIST]
[*]     [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]Will now halt[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] 
[/LIST]
  [FONT=SimSun][SIZE=4][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2][14412.320600] mei_me [/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]0000[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]:[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]00[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]:[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]16[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2].[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]0[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#ffffff][FONT=SimSun][SIZE=4][COLOR=#00000a][FONT=Courier New][SIZE=2]: stop 
[14412.321229] reboot: System halted[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

I've seen that some posts asks for details from /etc/default/grub, so here's what mine looks like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop"
GRUB_GFXMODE=1280x768x24

Hope you can help, Thanks.

---

### Post by grahammechanical on 2013-11-02
Ubuntu sits on top of Linux which is a command line OS. So, when we load Ubuntu it is Linux that first loads and then Ubuntu loads on top of that and we get a login screen or a desktop if we have automatic login set.

When we first shut down Ubuntu it is Ubuntu that shuts down. Linux is still running. It has to stop various Linux processes. This is nothing to do with Grub. Grub is just a boot loader. I know that Grub developers do not like Grub being called "just" a boot loader. But that is what it does and then Grub is gone.
 
We get those shutdown messages because that is the way that Linux works. There are a lot of similar startup messages when we load Ubuntu but they are mostly hidden by a splash screen. It is possible to load a splash screen during loading of Ubuntu but once Ubuntu has shut down the splash screen disappears and we get a look behind the scenes and we see Linux.

This is the way it is. Remember, that a Linux distribution is a collection of components developed by different groups of people. They all have to fit together. It is a very different development process in comparison with operating systems that we have to buy. Actually, I do not buy. I choose not to use them.
 
Regards.

---

### Post by mal_skelton on 2013-11-02
Thanks for your speedy reply [[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323"). I'm taking from what you say that the messages are all normal and nothing to worry about. That's good but is there anything I can do to hide these same messages so they don't flash on the screen before the white dots when shutting down?

---

### Post by ian-weisser on 2013-11-02
There is currently no setting, no option, no checkbox, to hide those messages or otherwise prevent them from flashing on your screen.

---

### Post by mal_skelton on 2013-11-03
Okay, thanks for your reply [[COLOR=#000000]ian-weisser[/COLOR]]("http://ubuntuforums.org/member.php?u=1841707"). I shall now regard this query as resolved.

---

