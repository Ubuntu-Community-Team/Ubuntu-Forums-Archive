---
title: "Online Accounts / Keyring Issue"
date: 2017-04-16
forum: Desktop Environments
---

### Post by Eldon_McGuinness on 2017-04-16
I am having two issues with The Gnome Online Account Manager, from a fresh install of Ubuntu Gnome 17.04, and would appreciate any help that is offered.

First off, whenever I try to add my gmail account to the Gnome Online Accounts Manager it does not work properly, it consistently tells me my credentials are expired. I have verified my password and also tried to remove the gnome/gmail association on the gmail site. You can see this in the images below: 
[http://i.imgur.com/3Tt89Fx.png](http://i.imgur.com/3Tt89Fx.png)
[http://i.imgur.com/9yDRdit.png](http://i.imgur.com/9yDRdit.png)

The second is when I remove an account from the Online Account Manager I receive another error telling me it could not be done. I have tried to delete the keystore via seahorse and via cli, in both instances, once I add an account back and try to remove it I get the same error.
[http://i.imgur.com/JToVXul.png](http://i.imgur.com/JToVXul.png)

---

### Post by Habitual on 2017-04-17
You don't happen to auto login to the desktop, do you?
I am not clear if that is a feature of the Ubuntu Desktop offering or not.

I've seen and had vague and various anomalous key activity caused by auto logging in to the desktop.

Just sayin'

---

### Post by Eldon_McGuinness on 2017-04-17
No I don't, but I do have an update on this.

When I login I am not able to create the accounts as noted above, however, if I run the following command everything works as expected.

```
/usr/lib/gnome-online-accounts/goa-daemon --replace
```

I threw this in my startup applications and it seems to fix the issue, whatever that issue is. I'm going to leave this as unresolved as this is most definitely a fix, but instead an ugly hack to get around the issue.

---

### Post by Habitual on 2017-04-17
Well, I am not sure how you found that gem, but good job!

---

### Post by heatpumpcontrol on 2017-04-25
This worked for me. However I think this is being addressed as a Bug [https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1610944]("https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1610944")

---

### Post by lagomazzini12 on 2017-09-29
This worked perfectly for me:
pgrep goa-daemon | xargs kill -9

---

