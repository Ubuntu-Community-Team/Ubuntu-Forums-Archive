---
title: "Laptop Locations (Environment setup by location)"
date: 2009-04-13
forum: Desktop Environments
---

### Post by hevysighs on 2009-04-13
Is there any good ways of setting up your environment depending on the login "location"?  Right now I end up changing my HTTP Proxy settings several times a day, at work there is a proxy and at school and at home there is not.  I also have file servers at work that I use regularly but none at school, however I do have a backup device at home and my wifes Mac.   I guess I would think the majority of my configuration should be handled with NetworkManager however it's not hooked into HTTP proxy that I can tell.  What I'm really wondering is if there is some way to specify a particular login script to run when login happens.  I guess this would have to be a gnome WM feature, like a popup for "location".  Any ideas?  Thanks in advance.

---

### Post by hevysighs on 2009-04-15
I have two scripts now for home and work that I "source" every time I'm either at home or at work.  They setup the general http_proxy, create a .ssh/config and .subversion/servers.  I was hoping to be able to add a dialog button to the login to choose a script to run that would be nice.  The problem with sourcing the script is that I have to run it in every shell that I start.  Maybe I just need to have two terminal profiles to launch a shell w/ each script?

Maybe there is a better way of doing this, Any ideas?
Here's my home script
#!/bin/sh
echo "Home Script Removing HTTP Proxies"

SSH_CONFIG=.ssh/config
echo "rm $SSH_CONFIG"
rm $SSH_CONFIG

SVN_SERVERS=.subversion/servers
echo "rm $SVN_SERVERS"
rm $SVN_SERVERS

echo 'unset http_proxy'
unset http_proxy

---

### Post by hevysighs on 2009-04-16
What I really want is to create a new gnome session.  But when I follow the instructions there is no create button in the gnome-sessions gui (System->Preferences->Sessions).  Enough talking to myself I'll take it to gnome.

---

