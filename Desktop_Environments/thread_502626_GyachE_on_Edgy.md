---
title: "GyachE on Edgy"
date: 2007-07-16
forum: Desktop Environments
---

### Post by smacd on 2007-07-16
So I've gotten GyachE Improved installed, but I am having a little problem that seems to be preventing me from logging in.

when I load up GyachE, the following appears in the left window:
> GyachE Improved 1.0.5 
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)
 Plugin Loaded:  'Blowfish-Internal' 
 Plugin Loaded:  'GyachI-Photos' 
 Plugin Loaded:  'MCrypt' 
** Plugin '/usr/local/share/gyachi/plugins/gyachigpgme.so' could not be loaded because of an error:

An error occurred initiating the plugin.
System Requirements: GpgMe (gpgme 0.3.16 or better), GPG 1.0.7 or better

Location: /usr/local/share/gyachi/plugins/gyachigpgme.so
** Plugin Loaded:  'GyachI-XMMS' 
 Loaded 4 plugins from '/usr/local/share/gyachi/plugins'.


Also, what appears is the login dialog, the user-name, password, chat room, login button, etc. But I can't seem to actually login, and I believe it is because of the above problem.

So, I have since downloaded and installed (manually) gnupg-1.4.7, gpgme-1.1.4, and libgpg-error-1.4. However it is still not working.

Can anyone help?

---

### Post by loell on 2007-07-19
those are just optional plugins,  but you can actually login.

select the server to login in the login window, 

enter you username and password, 

check the no chatroom.

and click the login button.

---

