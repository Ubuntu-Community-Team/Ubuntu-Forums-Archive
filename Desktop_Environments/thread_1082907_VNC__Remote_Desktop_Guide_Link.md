---
title: "VNC / Remote Desktop Guide Link?"
date: 2009-02-28
forum: Desktop Environments
---

### Post by Corrupter on 2009-02-28
can someone please point me to a guide for vnc server / remote desktop.

Let me clarify, i know there are a ton of them out there, all pointing to how its juyst a simple check box here and there and voila, install realvnc or freenx and you got yourself a remote desktop session.  however i am looking for a little more like this:

i need to remote desktop to the ubuntu machine without having to login on it first.  it has to be a full gui interaction like what vnc offers preferably with little packages installed on the ubuntu box.

furthermore i would love to be able to use the remote desktop from other ubuntu AND windows machines to log in to it.  i realize the windows machines will need an app like realvnc or freenx which is fine, however i also use SSH from time to time and want to do x11 forwarding over ssh when i just want to run an app or two and not the whole ubuntu desktop so if there is a windows app that will allow the ability to ssh in and be an x server to port selected apps via terminal or i can choose from the same program the option to vnc in that would be great.

im just trying to consildate the applications i have to load and manage on both my ubuntu machines and the few windows machines i run.

just so you know, i did search the ubuntu forums for the following terms and didnt find what i was looking for.

vnc without logging in
remote desktop without logging in

lastly does anyone know what i have to do to remote desktop a windows machine from ubuntu.  that would be something i'd like to throw in.

Thanks in advance,
Corrupter

---

### Post by Corrupter on 2009-02-28
I seem to have found something that gets me moving in the right direction.  I installed Xming on my windows machine and it allows for calling x-apps from ssh which is nice as well as remote desktop via xdmcp which seems to work nicely however i had a few questions if anyone knows anything about it.

First off, i was noticing that when i call the desktop remotely using xdmcp that it brings up the gnome desktop manager which houses a list of usernames that are on that machine.  if someone were to call up that system randomly i wouldnt want them to have a list of usernames on that machine.  any way to hide that list of usernames so that the authentication at gnome desktop manager requires them to type in both a username and a password?

lastly, i like how this seems to work from a windows machine, however my knowledge of working linux is a bit shat at best and was wondering how i would access a linux machine in the same fashion as i have described above from another linux machine similiar to how i did with the windows box?

thanks all for your help, i googled hide usernames in gnome desktop manager but didnt find what i was looking for.

---

