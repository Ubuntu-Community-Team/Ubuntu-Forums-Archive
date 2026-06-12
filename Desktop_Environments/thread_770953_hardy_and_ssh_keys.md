---
title: "hardy and ssh keys"
date: 2008-04-27
forum: Desktop Environments
---

### Post by benguin on 2008-04-27
Hi there,
I recently upgraded from Gutsy to Hardy (final), and ran into this annoying issue with ssh keys.

In Gutsy, I installed Seahorse for key management, and I had ssh keys (with passphrases) set up for keyless entry to a remote computer. By some magic (I will confess my ignorance here) everytime I logged on to Gnome, it was never required to enter passphrases again, as simple ssh from a terminal to those machines worked like a charm. This is a very important feature for me, since I use SVN tools like Kdesvn for code check in and check out, and kdesvn can be a pain if keyless entries are not set up properly. Before Seahorse, I had to manually add the keys to a running ssh-agent using the keychain program.

That said, after upgrading to Hardy, this ability just went away. I have no idea what happened, but even keychain does not seem to work. I still have a Gutsy box, and the same public-private keypair works from that box, but does not work from any Hardy boxes (I upgraded two). I looked at the Gnome keyring manager and all the access keys seem to be added there, but even then it is not helping me with keyless logins.

Is there something fundamental in Hardy that's been changed? I admit I have not been up to date with all the changes with Hardy, but I need this ability badly. Any help would be greatly appreciated.

Thanks,
-J-

---

### Post by mishek on 2008-06-17
I had this problem to.
This link help me: [http://live.gnome.org/GnomeKeyring/Ssh](http://live.gnome.org/GnomeKeyring/Ssh)

---

### Post by foresto on 2008-06-24
The automatic use of your ssh key comes from an "ssh agent".  For quite a while, the ssh-agent program that came with openssh was the usual implementation, but recent versions of gnome-keyring-daemon can also serve the purpose.

When an ssh agent has your private key loaded, running "ssh-add -l" should print a line of information about that key.  I'm guessing that it prints nothing on your hardy boxes.

Take a look in ~/.xsession-errors.  Does it contain a message that reads something like "another ssh agent is running"?  That's what tipped me off when I had a similar problem.  It turned out that ssh-agent was being automatically started early in hardy's X session startup scripts, which kept gnome-keyring-daemon from doing the same job.

Things I had to change:

- Comment out the use-ssh-agent line in /etc/X11/Xsession.options
- Delete the files in ~/.gnome2/keyrings
- Reboot (or maybe just restart gdm, or log out and back in).

Then, after logging in, entering my ssh key passphrase, and checking a box to remember it, just once, all further logins had this stuff automated.  Also, "ssh-add -l" printed a line of text assuring me that my ssh key was loaded.

---

### Post by centyx on 2008-07-11
> **foresto said:**
> 

- Comment out the use-ssh-agent line in /etc/X11/Xsession.options
- Delete the files in ~/.gnome2/keyrings
- Reboot (or maybe just restart gdm, or log out and back in).



I've followed the above instructions, and also removed the *.keystore files from ~/.gnome2/keystore.

On first relogin, gnome-keyring-daemon didn't set SSH_AUTH_SOCK or SSH_AGENT_PID, so ssh-add failed. 

I manually set SSH_AUTH_SOCK to the keyring-daemon's "ssh" socket file and set SSH_AGENT_PID to keyring-daemon's pid, and reran ssh-add.  I was prompted for the passphrases, both by ssh-ask-pass and gnome-keyring-daemon.

So I logged out and logged back in. SSH_* were still not being set correctly, so I set them by hand again. This time, ssh-add launched ssh-askpass, but not gnome-keyring-daemon's prompt. 

Upon examining my keyring with seahorse, I can see that the keys are there and the correct passphrases are saved.

Any ideas why

1) SSH_* environment variables aren't being set by gnome-keyring-daemon ?

2) I am still prompted for my passphrase by ssh-askpass even though the keys are saved in my keyring ?

Thanks!

---

### Post by centyx on 2008-07-11
I failed to mention that I was trying to use slim ( and start gnome-keyring-daemon from within openbox's autostart.sh ) instead of gdm. 

I've switched to gdm and it's working now.

Maybe another day I'll try again to get it working with slim.

---

