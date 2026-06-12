---
title: "The Authentication Dialog doesn't show"
date: 2015-11-19
forum: Desktop Environments
---

### Post by Musoy on 2015-11-19
Hi, there. When I try to update the softwares in 'Software Updater', it would stuck at 'Waiting for authentication' but no authentication dialog shows. Then I try to install and remove softwares in 'Ubuntu Software Center' but cann't do either, same happens where no authentication dialog. It seems that any GUI applications that need authentication wouldn't be able to work. This is the error when I try to add a new user. 

"An error occurred while checking for authorizations: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
You may report this as a bug."

Does anyone know how to fix this problem? Thanks in advance
p.s. authentication in the terminal works fine

Probably found the rough cause. Previously I add vncserver in ~/.profile. After commenting this command, the authentication problem disappear. It's rather puzzling.

---

