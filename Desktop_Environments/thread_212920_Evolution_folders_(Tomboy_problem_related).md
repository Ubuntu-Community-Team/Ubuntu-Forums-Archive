---
title: "Evolution folders (Tomboy problem related)"
date: 2006-07-10
forum: Desktop Environments
---

### Post by sprocket87 on 2006-07-10
I installed Tomboy today (method: apt-get install; distro: Ubuntu 6.06). So far it is a beautiful and intuitive program. I was excited to see the Evolution mail link plugin, so that was one of the first things I tried to use. It is supposed to be completely drag-and-drop: Drag an email from Evolution into the Tomboy note you want a link created in, and it makes the link for you. 

Unfortunately it didn't work right. I dragged an email from Evolution into one of my Tomboy notes and it generated the text link successfully. However when I tried to open the message by clicking the new link it brought up an error message: "Error while Opening folder mbox:/home/jessek/.evolution/mail/local#personal/Inbox. Cannot get folder `personal/Inbox': folder does not exist." My username is "jessek" for reference.

I think it is a problem with my Evolution setup, but I'm not sure. The only email account I'm using in Evolution is tied to my office's MS Exchange server. It almost seems like Evolution hasn't created a local, offline folder for my messages. I set the Inbox folder up to "Copy folder content locally for offline preparation", but it didn't help. I also made sure that my Mail Account Settings > Receiving Options had "Automatically synchronize account locally" checked.

Are there any suggestions for getting this to work? Thanks very much!


Jesse

---

