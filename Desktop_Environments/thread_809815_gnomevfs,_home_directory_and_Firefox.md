---
title: "gnomevfs, home directory and Firefox"
date: 2008-05-27
forum: Desktop Environments
---

### Post by arizonagroovejet on 2008-05-27
Where I work with have home directories mounted from a remote server at login using autofs. Occasionally, for various reasons, a user will log in and their home directory cannot be mounted. This results in errors and the user getting kicked back to the login screen and not knowing what happened. So I've worked out a way to detect such cases, create a directory locally, set $HOME to that directory and then start up a nice graphical session. That way people can at least get something done whilst the reason their home dir is not mounted is sorted out.

My problem right now is that Firefox does not work in this scenario. I've eventually managed to learn that it doesn't work because Firefox uses gnomevfs and gnomevfs does not respect the convention of using the value of $HOME to reference the user's home directory but instead uses getent. getent of course returns were the user's home dir should be, i.e. /home/username, not where it actually is. Hence gnomevfs attempts to create the directory /home/username/.gnome2 and this fails because /home/username does not exist and nor can it be created.


So... anyone have any idea how I can get Firefox to work in the scenario? Maybe there is some way I can make Firefox run without gnomevfs (short of compiling from source which I'm not getting in to)? Maybe there is some way to override gnomevfs's insistence of using getent rather than $HOME? I have of course looked in to both these approaches but drawn a blank.



I'm aware this is arguably quite off topic since it isn't Ubuntu related. However this is a high traffic forum where as Gnome's official forums seem almost deserted, my request to sign up there is awaiting manual approval and I figure someone may who hangs out here many have an idea.

---

