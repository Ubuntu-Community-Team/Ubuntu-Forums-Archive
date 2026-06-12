---
title: "Mounting An FTP File System"
date: 2006-01-15
forum: General Help
---

### Post by ajwagner777 on 2006-01-15
Does anyone know of any software that will alow you to mount an FTP file system?  I tried FTP mount, but I had difficulties getting it installed.  Can anyone give me some advice on how to go about doing this.
Thanks!
Aaron Wagner

---

### Post by hw-tph on 2006-01-15
I have never had much luck with FTP mounting, and besides that - it's insecure and probably a bad idea to use over the Internet. [shfs](http://shfs.sf.net) is a kernel module that lets you mount a remote  share using scp/ssh - secure and easy.


H&#229;kan

---

### Post by Matt Yun on 2006-01-15
You should use [FUSE]("http://fuse.sourceforge.net"), which is a kernel module to implement userland filesystems.   With FUSE, you can mount a remote FTP server as a local filesystem.  A list of FUSE filesystem projects can be found here:  [http://fuse.sourceforge.net/wiki/index.php/FileSystems]("http://fuse.sourceforge.net/wiki/index.php/FileSystems")

FUSE is included with the Linux kernel as of 2.6.14, but since Breezy uses 2.6.12, you will have to install it separately.  I think you can find it from Synaptic, but I always use apt-get.  Open a console, execute 'sudo su' to become root, then do the following at the prompt:

[B]root# apt-get update && apt-get install fuse-source fuse-utils sshfs
root# module-assistant prepare
root# module-assistant build fuse && module-assistant install fuse
root# modprobe fuse[/B]

Once you have FUSE installed, you can then select any type of filesystem to install.   In your case, you will probably be interested in [Fuseftp]("http://wiki.thiesen.org/page/Fuseftp").  (Disclaimer:  I have never used Fuseftp, so I can't help you there).

One of the posts above suggested that you use ssh instead of ftp, which is what I do.  For this, you need a FUSE module called sshfs.  Fortunately, you can install this from the standard Ubuntu apt-get repositories as well.  In fact, if you followed the above apt-get command, you've already installed it!

The only prerequisite for sshfs is that the remote server must have an ssh server enabled, and the local computer must have an ssh client (the default for most Linux distros).  This makes sshfs extremely convenient (especially compared to NFS) because you don't have to do any other configuration to your server to use it; and it's more secure to boot.  I keep my digital media on a server in the closet, and mount it from around my home using sshfs; this filesystem is good enough to watch videos or listen to mp3, even over wireless 802.11b, in my home network.

Put the following line in your local computer's /etc/init.d/bootmisc.sh file so that your local computer will automatically mount your sshfs filesystem on boot:

**/usr/bin/sshfs username@serverhost:/remotemount /localmount -o allow_other**

This assumes that you have an account on the remote server, and you've exchanged private keys so that you can ssh into the server without having to type a password.  The '-o allow_other' option permits all users on your local computer to access the sshfs mount; read the sshfs manpage for an explanation of other options.

EDIT: heh, I just noticed someone has already done a HOW-TO on this subject:  [HOWTO: Mount SSH Shares]("http://ubuntuforums.org/showthread.php?t=103860")

---

### Post by ajwagner777 on 2006-01-15
Thanks for your reply.  I cannot use any other protocol other than FTP because of the server im mounting.  It is a cable TV ad inserter and the only way they allow file transfers is over FTP.  I am planning on pairing this with rsync to auto upload new spots to my equipment.  When I get to work tomorrow i'm gonna give FuseFTP a shot.  Thank you for your help!
Aaron Wagner

---

