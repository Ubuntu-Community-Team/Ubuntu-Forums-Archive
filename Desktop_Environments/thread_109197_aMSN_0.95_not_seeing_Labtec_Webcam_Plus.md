---
title: "aMSN 0.95 not seeing Labtec Webcam Plus"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Galoot on 2005-12-28
I'm *this* close to talking my wife into allowing Ubuntu on the family PC. The only hurdle left is finding an IM program with decent webcam support for my daughter. (I know about Mercury. It's too big and boggy for their older PC, so I haven't even tried it with this cam and don't intend to.)

I downloaded aMSN 0.95, hoping for the best, but it's not seeing the webcam.

Here are the steps I've taken:
[list]
[*]Downloaded amsn_0.95-2.ubuntu.deb
[*]sudo dpkg -i amsn_0.95-2.ubuntu.deb
[*]Followed [this HOWTO](http://ubuntuforums.org/showthread.php?t=75284&highlight=amsn+webcam) to get Ubuntu Breezy working with the webcam
[*]Did "sudo ln -s /dev/video0 /dev/video"
[*]Opened the proper ports on my firewall for the webcam
[*]Ran gqcam to check if Ubuntu saw the cam (it did)[/list]
When I go into aMSN's "Configure Webcam" dialog it tells me my ports are well configured, the Webcamsn extension is loaded, and Capture Extension -capture- is loaded. All seems well.

When I click on "Change video settings" I am prompted to choose a device. I only have the one webcam, so I select it (V4L: Labtec Webcam Plus). Then I am prompted to choose a channel. Again, I have only one choice (SPCA561). At that point I get the following error message

> Error opening device
I decided to try chatting, with cam, anyway. The remote user could accept my invitation to view the cam, but only got a blue square, no pic. When opening the "Change Video Settings" dialog *after* this, aMSN told me it couldn't find the cam.

Here's the terminal output from this session:
> galoot@breezy:~$ amsn
playing /usr/share/amsn/skins/Ubuntu (Human)/sounds/online.wav
dlsym[./utils/linux/capture/libng/plugins/drv0-v4l2.so]: ./utils/linux/capture/libng/plugins/drv0-v4l2.so: undefined symbol: _ng_plugin_init
dlsym[./utils/linux/capture/libng/plugins/drv1-v4l.so]: ./utils/linux/capture/libng/plugins/drv1-v4l.so: undefined symbol: _ng_plugin_init
WARNING: no plugins found [/home/toma/amsn-0.95]
bgerror failed to handle background error.
    Original error: expected integer but got ""
    Error in bgerror: unable to convert date-time string "5//20/12/0 05::00"
playing /usr/share/amsn/skins/Ubuntu (Human)/sounds/type.wav
galoot@breezy:~$

I'm getting annoyed. gqcam can see the webcam but aMSN can't. Any ideas?

(BTW, what is this?
"WARNING: no plugins found [/home/toma/amsn-0.95]"
Who the heck is toma? There's no such user on this PC.)

I've also posted this to the aMSN boards. I'll update this thread if they figure it out, and vice-versa.

---

### Post by Stemp on 2005-12-29
Hi Galoot,

My Labtec Webcam Pro work like a charm in aMSn. But I can't find the Webcam Plus in the [spca5xx's list]("http://mxhaard.free.fr/spca5xx.html")
The **lsusb** command gives you what ? 
Also, did your cam works with GnomeMeeting ?

---

### Post by Galoot on 2005-12-29
Thanks for the reply, but I missed my chance to install Ubuntu on their machine, so I'm no longer trying to troubleshoot the camera with Linux.

FWIW, though, Windows 98 *also* has problems with it. :razz:

---

### Post by Smittey on 2006-05-07
I am having the same problem with my Logitech Quickcam sphere, but that one does not give me problems in Windows. Anyone got a tip on it?

---

### Post by Marco Bresciani on 2006-08-30
Almost the same problem here... could you please explain me how you managed firewall? I'm not so expert. I've tried to follow the FAQ on aMSN page but two things happens:
 - if I use the "default" configuration for firewall (actually is port forwarding for ADSL ethernet modem) aMSN says I'm behind firewall and doesn't work;
 - I tried some configurations on firewall... and aMSN says everything ok... but that I have no device! :-(

camorama and gqcam work perfectly... even if a bit dark.

Could you help me please?

---

### Post by hooked on 2007-01-16
I have a Logitech Quickcam Communicate STS, and I get the same error message with aMSN as the first post. When I click the "configure webcam" button it says:
Type: Firewall
Listening: false
Your ports are well configured
Webcamsn extension is loaded
Capture extension-capture-is loaded

I can't figure this out, and I've been trying for quite some time.

---

