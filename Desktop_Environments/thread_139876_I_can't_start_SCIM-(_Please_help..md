---
title: "I can't start SCIM:-( Please help."
date: 2006-03-05
forum: Desktop Environments
---

### Post by t_huankiat on 2006-03-05
Hi guys, hope I can get some help here. I just started using Ubuntu. Today I tried to enable foreign language input in Ubuntu. So I did a google and found out this website:
[http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/")
without realizing that's for 5.04, I just followed the instruction blindly.
The installation was good, but when it came to the following instruction:
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup
I have no idea what I was doing. After I typed the above commands, I tried to open SCIM with control+space, it didn't work. So I went back to System->Preference for the SCIM menu to see what's did I do wrong. That didn't help, so I thought I didn't type the above commands correctly and so I re-typed them again.

OK... now I can't even open SCIM. It just apeared to be launching but never open. It did open before, so I guess I did screw up something that I'm not aware of. Can anyone tell me what I did wrong? Is there anyway to reinstall or undo the part I screwed up?:cry:

---

### Post by t_huankiat on 2006-03-05
OK, I was being stupid. I already had SCIM installed. So I just remove all the mentioned package the SCIM reloaded!
Now back to square one and I'm happy...:-D

---

