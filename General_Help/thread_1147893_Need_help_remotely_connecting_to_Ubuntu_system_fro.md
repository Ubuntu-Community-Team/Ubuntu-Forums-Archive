---
title: "Need help remotely connecting to Ubuntu system from Windows"
date: 2009-05-03
forum: General Help
---

### Post by jimbo6846 on 2009-05-03
*I posted this in the Networking & Wireless board earlier today, but I don't think that's the right place to ask. All the posts there seem to be about getting your network connection going and before I knew it, my post fell to page 4 with hardly any views at all. So, I'm reposting here hoping someone here can help me.*
 
 
Hi guys, I'm incredibly new to Linux (2nd day working with it, hehe) and I'm having some trouble getting my Ubuntu set up to work without a monitor and keyboard/mouse.
 
A little background:
 
I have multiple other systems in the house that I want to use to connect to this Linux box, all of which have windows Vista or XP installed. On my Ubuntu machine, I have installed and configured vncserver as well as enabled the XDMCP protocol. On my windows machines, I have installed UltraVNC (TightVNC would simply NOT work. Nothing but a gray desktop that was not functional at all. after hours of troubleshooting, I gave up and installed UltraVNC on my Vista machine and it worked just fine.) as well as Xming. UltraVNC connects just fine, but requires that the machine already have a VNC user logged in, otherwise it won't connect. Xming doesn't require that a user be logged in, but it creates it's own sessions and as far as I can tell, there is no way to get those sessions to stay open when closing the Xming window. 
 
What I basically want to do is this: I want to be able to remotely connect to this linux box no matter if someone is logged in or not and I want that session to remain open if I close the remote window, just like RDP for the Windows environment. Is there any way to do this, because it seems like neither vncserver nor Xming are capable of this.
 
Do I need a different OS? I installed the "desktop" version of Ubuntu 9.04. Should I install the "server" version instead? Any help/suggestions are very much appreciated. Let me know if any more info is needed. Thanks in advance.

---

### Post by jimbo6846 on 2009-05-04
Can anyone help me with this?  I'm starting to wonder if what I'm looking for is even possible when coming from a Windows machine... :(

---

### Post by mannheim on 2009-05-04
I use nx from nomachine. There are probably good how-to's on the forums if you want to try this, but basically you need to install (on the linux machine) the ssh package as well as the packages for nx-client, nx-node and nx-server from nomachine's website. Then install nx-client on the client machines (also from nomachine's website). The clients will need to have ssh access to the linux machine.

With this setup, you can start a session on the linux machine from any one of the clients (without a previous local login on the linux machine). You can "disconnect" the client's session, and reconnect later from that or another client machine.

I'm sure this is not the only solution; perhaps not the best. But it's what has worked for me.

---

### Post by geirha on 2009-05-04
Try this guide: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

The difference between the desktop and server version of Ubuntu is not that big. Both use the same repositories and can run all the same applications. Probably the biggest difference is that the desktop version comes preinstalled with Xserver and Gnome, while the server version doesn't.

---

### Post by jimbo6846 on 2009-05-04
geirha,

Thanks for the response.  I was actually in the middle of trying to get FreeNX configured last night before I finally took a break and called it a night.  I will continue to try getting FreeNX working when I get home from work today.

I do have a couple questions while I wait in anticipation though:  Does FreeNX require a user to be locally logged into the machine in order for a connection to be established (this seems to be the case with VNC)?  For example:  Say I'm working on the box through a remote connection; there's no monitor, keyboard or mouse physically connected to this computer.  Now, I make some changes that require me to reboot the computer (or I just feel like rebooting).  With FreeNX, could I remotely reboot the computer and then log back in remotely when it comes back up?  Also, if I remotely log into the computer with FreeNX and then close the session window, does the session stay open or does it close automatically (Xming closes the entire session.  I couldn't find a way to keep the session going when closing the window).

---

### Post by jimbo6846 on 2009-05-04
> **mannheim said:**
> I use nx from nomachine. There are probably good how-to's on the forums if you want to try this, but basically you need to install (on the linux machine) the ssh package as well as the packages for nx-client, nx-node and nx-server from nomachine's website. Then install nx-client on the client machines (also from nomachine's website). The clients will need to have ssh access to the linux machine.

With this setup, you can start a session on the linux machine from any one of the clients (without a previous local login on the linux machine). You can "disconnect" the client's session, and reconnect later from that or another client machine.

I'm sure this is not the only solution; perhaps not the best. But it's what has worked for me.

mannheim, thanks for the response.  I didn't see this before responding to geirha.  From the sound of your post, it seems like FreeNX is capable of doing what I'm looking for.  Keeping my fingers crossed that he speed of the connection is fast enough so that the response-time is faster than the 2+ seconds I see when I click on items through Xming.

---

### Post by HermanAB on 2009-05-04
Howdy,

Solutions like VNC and FreeNX are *not* the best way to manage a server.  The industry standard way to manage Unix machines is to use SSH.  Once you have SSH up and running, you will quickly realize why.

On Linux, install the ssh-server package (it may already be installed).  On Windows, use Xming and PuTTY.  Google for Xming, there should be a link from there to PuTTY, but PuTTY is made by Greenend.

SSH can do everything VNC does and more, and it is secure.  

VNC is mainly a Windows thing - it is also good for training, but it is not good for managing a server and it is totally insecure, so it is a good way to get your server hacked.

---

### Post by geirha on 2009-05-04
NX is like connecting to the server through ssh with X11 forwarding, and starting an X session, except it adds some compression and caching making it much more smooth.

---

### Post by jimbo6846 on 2009-05-04
UPDATE: I currently have freenx installed on the linux server (just a personal toy-around-with server, nothing professional or commercial about it). I am connecting to the linux server through freenx with ssh authentication... *I think*. What is happening is I run the NX Client for Windows on my Windows box. I've configured it to connect to my linux box on Port 22 (for some reason, I couldn't get my custom port of choice to work). In the NX Client box I use the username and password of my local account on the linux box (I used **ENABLE_USERMODE_AUTHENTICATION="1"** and **ENABLE_SSH_AUTHENTICATION="1"** in the /etc/nxserver/node.conf file. The other options I left off). This works for me and I'm able to use the NX Client to connect to the Linux box. However, the session that starts doesn't seem to actually use my local account credentials. I don't have access to files and folders that this local account is the owner of. Can anyone help me remedy this problem? Please let me know if you need me to elaborate on what I'd like to do a little more. 
 
Also, does this mean that I'm actually using SSH for the connection, or is the ENABLE_USERMODE_AUTHENTICATION="1" option changing that?
 
Again, thanks for the replies/help guys. I really appreciate it.
 
EDIT:  I forgot to add to HermanAB, I was using Xming to connect to the linux box, but it was *incredibly *slow.  Far beyond what I'd call acceptable.

---

### Post by geirha on 2009-05-05
If you open a terminal and type ```
echo $USER $HOME
``` Does it show the correct username and homedirectory?

Also, type in a terminal, without hitting enter yet (and without the quotes): "ls -ld "
Make sure there is a space behind it, then find a file or folder you don't have access to, but should've had access to, in nautilus (the file explorer), and drag it over to the terminal window. The full path of the file/folder will be inserted at the end of the command you started. Hit enter in the terminal and see what permissions and ownership it has.

---

### Post by mixmaster on 2009-05-05
If you are happy with command lines, you can just use ssh - there are a lot of free ssh clients around and some commercial software.

NX will give you ssh + x-forwarding + compression.  It is very good for logging into remote systems over the internet but is probably overkill for a home network since you probably don't need the compression.

Personally I'm lazy.  I installed Virtualbox on my windows system and installed ubuntu in it.  Then I use XDMPC to access the remote ubuntu box.

---

### Post by jimbo6846 on 2009-05-05
> **geirha said:**
> If you open a terminal and type ```
echo $USER $HOME
``` Does it show the correct username and homedirectory?
 
No, it just repeats what I type. Here's what it says when I open a Terminal window:
 
*HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)*
*NX> 105*
 
When I type "echo $USER $HOME" and hit enter, the result is this:
 
*NX> 105 echo $USER $HOME*
 
> Also, type in a terminal, without hitting enter yet (and without the quotes): "ls -ld "
Make sure there is a space behind it, then find a file or folder you don't have access to, but should've had access to, in nautilus (the file explorer), and drag it over to the terminal window. The full path of the file/folder will be inserted at the end of the command you started. Hit enter in the terminal and see what permissions and ownership it has.
 
Doing that does has the same result as the echo command from above, it just keeps repeating what I type, rather than execute the commands.

---

### Post by geirha on 2009-05-05
I meant opening a terminal inside the logged in session. Applications -> Accessories -> Terminal

---

### Post by jimbo6846 on 2009-05-05
> **geirha said:**
> I meant opening a terminal inside the logged in session. Applications -> Accessories -> Terminal

Do you mean on the local computer itself?  Because I don't see the relevance in that, logging in locally works fine.

If you mean the session that is created when I log in with the NX Client, then that is what I posted.  I connected with the NX Client to the linux box, using my credentials for the account I created when I installed Ubuntu, which allowed the session to be created.  However, the session that is actually created seems to be some kind of generic NX session that doesn't have Terminal rights or something, because no matter what commands I type in the terminal window, the terminal just repeats my line back to me.

Let me know if you need more info.  I'm at work right now, so it'll be from memory, but I'll try to remember whatever I can.

EDIT:  Just in case you think it will help though, the **echo $USER $HOME **line resulted in

[I]$ echo $USER $HOME
james /home/james[/I]

As for the "ls -ld", I didn't end up doing it on the locally logged in account.  But while in the file explorer program (Nautilus I suppose, but I didn't see that name anywhere), I browsed to /home/james and then right-clicked on a folder I'd created called "Share" and went to the permissions tab.  The owner was the first name and last name of my user account.  However, when I log into the linux box locally, the username I use is just my first name, I don't put a last name in.

When I get home in a few hours, I'll add the results of the "ls -ld" command.

---

### Post by geirha on 2009-05-05
I'm unable to reproduce this as I don't have Windows. I tried setting ENABLE_USERMODE_AUTHENTICATION, but I'm unable to connect with either Nomachine's NX client nor qtnx after that. Try disabling that option.

---

### Post by jimbo6846 on 2009-05-05
> **geirha said:**
> I'm unable to reproduce this as I don't have Windows. I tried setting ENABLE_USERMODE_AUTHENTICATION, but I'm unable to connect with either Nomachine's NX client nor qtnx after that. Try disabling that option.

Setting ENABLE_USERMODE_AUTHENTICATION=0 or simply commenting that line out results in the NX Client for Windows giving me a message that says "Authentication for user James has failed".

I toyed around with those settings, and ENABLE_USERMODE_AUTHENTICATION=1 is the only setting that seemed to actually make a difference.  If I disable that option, no matter what the other options are set to, I get a "Authentication for user James has failed" message (at least as far as I can remember).  Disabling ENABLE_SSH_AUTHENTICATION or ENABLE_SU_AUTHENTICATION didn't seem to matter.  And the ENABLE_PASSDB_AUTHENTICATION, option had the same end result:  a generic user environment.

There must be some option somewhere that checks the credentials supplied to the NX Client and matches them against the list of local users and logs into that local user's environment.

---

### Post by geirha on 2009-05-05
Did you install [openssh-server](apt:openssh-server) on the server, and is it running? ```
sudo /etc/init.d/ssh start
```

---

### Post by jimbo6846 on 2009-05-05
> **geirha said:**
> Did you install [openssh-server]("apt:openssh-server") on the server, and is it running? ```
sudo /etc/init.d/ssh start
```

I did install openssh-server.  I configured it and left it set for port 22, because for some reason the other port I tried changing it to didn't work.  But maybe it wasn't working because I didn't have the freenx configuration right...  anyway, that's besides the point hehe.

but yes, openssh-server is installed and running, *I think.*  I don't remember typing sudo /etc/init.d/ssh start, but I did type /etc/init.d/ssh restart several times.

---

### Post by jimbo6846 on 2009-05-06
Alright, I got it working now.  I decided to just suck it up and start over with a fresh install of Ubuntu 9.04.  After the install finished, I immediately installed openssh-server and configured it for my desired port.  I then installed freenx and configured it for SSH authentication.  I tested it and it seems to be working fine now.  When logging in with my james account through NX Client for Windows, I get my regular desktop environment now.  Although it is a separate memory space from the locally logged in account, it's still the same environment, and changes made on one side cross over to the other side (which is kind of neat :) )
 
I guess I just fudged up some file somewhere before :(.  I've learned my lesson and am now creating .original backups of every file I alter.
 
Thanks for the help guys, I appreciate it :)

---

### Post by jeremy1138 on 2009-05-11
I'm having some trouble with getting some things to work through an ssh connection and this seems to be the right thread though I don't see an answer to my particular question.  The problem I'm having is that I'm unable to get gnome-panel to work on my client computer for some reason.  All I get is bars that show at the top and bottom of my screen and they will occasionally show some jumbled stuff.  They are not usable.  I am able to start Firefox without any trouble and it seems to work fine.  My client machine is running Windows Vista with PuTTY and Xming.  I have X11 forwarding enabled in PuTTY and for the X display location I've entered my client machine's local address (192.168.1.101).  On the server machine, which is running Ubuntu 9.04 (desktop version), I have installed openssh-server.  Can anyone shed some light on my situation?  Also, I should add that I have another computer, also connected to my home network, that is running Linux Mint 6 and I can run the gnome-panel command without any trouble using
```

ssh -X -C -c blowfish server@server1.local

```
to ssh into the computer and then using
```

gnome-panel

```
to get the gnome panels and much of the functionality of gnome desktop.  I'm not really sure if what I'm trying to do is even the best way to go about this but I'd like to get it working if I can.  I'm also open to suggestions if anyone has a better way to connect to this remote computer and get the desktop to show up on my Windows computer.  I also have vnc working between my two linux machines but I'd like to get out of using it.  Thanks!

[edit]
Also, Firefox seems really sluggish and it lags behind by like two seconds.  Is there a way to enable compression?

---

### Post by jeremy1138 on 2009-05-12
Well it appears that I've killed this thread along with the last few that I've commented in.  Perhaps I smell bad?

---

