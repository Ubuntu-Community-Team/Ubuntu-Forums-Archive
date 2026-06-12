---
title: "Unity3D and Gnome 3 &amp; remote desktop capabilities."
date: 2012-12-06
forum: Desktop Environments
---

### Post by bmullan on 2012-12-06
Unity 3d, Gnome3 ... both are going to break many of the popular methods of creating a remote desktop TO an Ubuntu machine (or any other linux Distro).

Note: this discussion is about remote desktop not rdesktop/rdp

With Ubuntu 12.10, Unity2D is no longer supported (as I understand it). 

Gnome just announced that with Gnome3 they are dropping support for "gnome-fallback".

Designed to work with real 3D hardware, Unity 3D uses the OpenGL library to send graphics commands directly to the video adapter, where data is rendered and shown on a "physical" display.

With Unity 3D the main problem is that an NoMachine's NX, x2go, VNC and others, the virtual session will not run on a physical display. My web searches on this so far seem to indicate that no workarounds are possible to eliminate the problem at this time.

NoMachine, x2go, the many VNC flavors of remote desktop are all trying to figure out WHAT could be done to move their remote desktop applications into this future.

Sending graphic objects to client requiring a lot of network bandwith... AND ... many tablet devices may not have the hardware or processing capabilities to support this.

Rendering 3D Graphic on the desktop "server" (this is the way as VirtualGL working) requires 3D Graphic Adapter on that server.

To me this will clearly impact the ability to Remote Desktop to:

1) nearly every "cloud" based compute instance, as none that I know of include a physical video adaptor.

2) many private enterprise, smb, data center machines (again no video adaptors)

3) and possibly many home computers if their video capability doesn't include a video adaptor with 3d support.

Can Canonical or anyone discuss what if any plans there are to address this ??

Note: I know you could install xfce etc but that doesn't seem to be a viable solution to me because it would force people to use a different desktop environment than what they may utilize on their personal or work PC/Laptop with the same Linux distro.

thanks
brian

---

### Post by grahammechanical on 2012-12-06
This is the wrong place to ask this question

> Can Canonical or anyone discuss what if any plans there are to address this ??

I doubt very much if you will get any 'official' answers.

I also wonder if you are looking at the remote access feature from the wrong direction. Surely, the purpose is to use the operating system (including the desktop) of one computer to access the file system on another computer.

I do not think that any graphic objects, as you put it, will be sent to the client. All graphic composition of the user's desktop will be done on the user's hardware and not by the client machine's hardware.

If this is not true, then how is it possible to have servers without graphic/video adapters in the first place? The World Wide Web would not be possible.

According to your reasoning remote access would not have been possible even before the dropping of low hardware specification desktop environments from Gnome and Ubuntu had taken place.

Why make Remote access easier in 12.10 if it did not work because the client hardware was not capable of running Ubuntu 3D?

I have just been watching a re-play of a television program by using a web browser. How was that possible? Was I using the video/graphic hardware in the servers of the television company? Was my machine sending graphic objects to those servers?

Someone, inform me. if I am wrong.

Regards.

---

### Post by bmullan on 2012-12-13
Maybe I'm misunderstanding your answer...

Note:  none of the following are canonical comments but sw engineers at several remote desktop applications

[URL="Here is NoMachine (NX) support writeup about the issue:  http://www.nomachine.com/fr/view.php?id=FR06I02466"]
http://www.nomachine.com/fr/view.php?id=FR06I0246[/URL]6

Also here is what another non-canonical developer wrote:

We know, that there is a problem running 3D Desktops with our remote desktop product. The same problem have also other remote computing protocols.

Both solutions suggested by NoMachine support have disadvantages.
Sending graphic objects to client requiring a lot of network bandwith.
Rendering 3D Graphic on server (this is the way as VirtualGL working)
requiring 3D Graphic Adapter on server.

But it is not just a problem with 3D Acceleration. The problem is also
with compiz. As you can see in link below:

[URL="http://sourceforge.net/projects/virtualgl/forums/forum/401860/topic/5425279"]http://sourceforge.net/projects/virtualgl/forums/forum/401860/topic/5425279
[/URL]

I'm not a graphics eng. but they do work in that area for their various products ... and they think its a problem.

As to remote desktop use... I do it every day to Ubuntu servers running in Amazon's EC2 cloud .. none of which have a graphics card.  I install ubuntu-desktop on those servers and access it remotely from work/home. It works as long as I use Unity-2d or Gnome with "gnome-fallback"... but disable either of those & it breaks.  

Who uses remote desktop apps? ... lots of people use Remmina, VNC, NX, FreeNX, x2go, etc.  Many LTSP users utilize NX.  

Simple remote desktop just involves setup of X with a framebuffer, which allows it to run, then you can SSH in, do X forwarding, and see a normal X11 session remotely.  Performance this way isn't great but it works.   

Most of the other apps implement some kind of major compression using jpeg, turbo-jpeg, etc to improve performance.

Another example of a headless remote server use could be to use Xvfb (X virtual framebuffer) to create a framebuffer in memory to which it renders graphic images.

Launch the X server using the following command on the server:

Xvfb :1 -screen 0 800x600x16 -ac

This will create a X server with a 800x600 screen on display :1 and disable access controls. You should probably launch this in the background.
 
And once the server is up, run an application which connects to display :1

The first app you'd probably want to run is some Window Manager (WM).

Lastly.. have you used KVM?  If so and you've installed say Windows XP as a virtual machine... KVM *emulates a Video card for you in software* (cirrus, vga etc).

Even with Windows Server 2012 you no longer need a dedicated GPU graphics card in the server to use RemoteFX.  RemoteFX vastly improves the quality of graphics over RDP. Windows Terminal Services uses a "*virtualized GPU* on standard server hardware.

---

