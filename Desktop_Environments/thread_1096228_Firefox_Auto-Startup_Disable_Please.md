---
title: "Firefox Auto-Startup Disable Please"
date: 2009-03-14
forum: Desktop Environments
---

### Post by cederer on 2009-03-14
Hello, I can't figure out why Firefox automatically starts up in the background when I start Xubuntu:


-I always close Firefox before shutting down.
-It's not listed in "Autostarted Applications" via Xfce settings
-"Automatically Save Sessions on Logout" settings is unchecked in
  Sessions and Startup via Xfce settings
-I suspect it has something to do with ~/.cache/sessions/xfce4-session-chris-laptop:0 ----> checkout client 6

```

[Session: Default]
Client0_ClientId=117f000101000123605354600000052400000
Client0_Hostname=local/chris-laptop
Client0_CloneCommand=xfwm4,--display,:0.0
Client0_CurrentDirectory=/home/chris
Client0_Priority=20
Client0_Program=xfwm4
Client0_RestartCommand=xfwm4,--display,:0.0,--sm-client-id,117f000101000123605354600000052400000
Client0_UserId=chris
Client1_ClientId=117f000101000123605354600000052400001
Client1_Hostname=local/chris-laptop
Client1_CloneCommand=xfce4-panel,--display,:0.0
Client1_CurrentDirectory=/home/chris
Client1_Priority=40
Client1_Program=xfce4-panel
Client1_RestartCommand=xfce4-panel,--display,:0.0,--sm-client-id,117f000101000123605354600000052400001
Client1_UserId=chris
Client2_ClientId=117f000101000123605354700000052400002
Client2_Hostname=local/chris-laptop
Client2_CloneCommand=Thunar
Client2_DiscardCommand=rm,-f,/home/chris/.cache/sessions/Thunar-117f000101000123605354700000052400002
Client2_Priority=24
Client2_Program=Thunar
Client2_RestartCommand=Thunar,--sm-client-id,117f000101000123605354700000052400002,--daemon
Client2_UserId=chris
Client3_ClientId=117f000101000123605355000000052400003
Client3_Hostname=local/chris-laptop
Client3_CloneCommand=xfdesktop,--display,:0.0
Client3_CurrentDirectory=/home/chris
Client3_Priority=35
Client3_Program=xfdesktop
Client3_RestartCommand=xfdesktop,--display,:0.0,--sm-client-id,117f000101000123605355000000052400003
Client3_UserId=chris
Client4_ClientId=117f000101000123605355200000052400004
Client4_Hostname=local/chris-laptop
Client4_CloneCommand=update-notifier,--sm-config-prefix,/update-notifier-Z1BzRk/
Client4_CurrentDirectory=/home/chris
Client4_Program=update-notifier
Client4_RestartCommand=update-notifier,--sm-config-prefix,/update-notifier-Z1BzRk/,--sm-client-id,117f000101000123605355200000052400004,--screen,0
Client4_RestartStyleHint=1
Client4_UserId=chris
Client5_ClientId=117f000101000123605355300000052400005
Client5_Hostname=local/chris-laptop
Client5_CloneCommand=gnome-power-manager,--sm-config-prefix,/gnome-power-manager-UXY3cw/
Client5_CurrentDirectory=/home/chris
Client5_Program=gnome-power-manager
Client5_RestartCommand=gnome-power-manager,--sm-config-prefix,/gnome-power-manager-UXY3cw/,--sm-client-id,117f000101000123605355300000052400005,--screen,0
Client5_UserId=chris
Client6_ClientId=117f000101000123605479800000052400016
Client6_Hostname=local/chris-laptop
Client6_CloneCommand=firefox,--sm-config-prefix,/firefox-a3i7ox/
Client6_CurrentDirectory=/home/chris
Client6_Program=firefox
Client6_RestartCommand=firefox,--sm-config-prefix,/firefox-a3i7ox/,--sm-client-id,117f000101000123605479800000052400016,--screen,0
Client6_UserId=chris
Count=7
LegacyCount=0
Screen0_ActiveWorkspace=0
LastAccess=1236057041


```

Xubuntu 8.10 intrepid
2.6.27-11 generic
Firefox 3.0.7

Related packages installed:
Firefox  <<<--?
Ubufox
Firefox-3.0  <<<--?
Firefox-3.0-branding

Thanks

---

### Post by jcallough on 2009-04-09
I am having the same issue.  Even worse, when I run htop I see that the first 4 processes using the most of my memory (17.7% each = over 70%) are firefox!

This is seriously slowing down the performance of my desktop and is a serious concern.

I am running Kubuntu 8.10 as well and have turned off all unnecessary features to speed up the rest of the environment.  If anyone has any suggestions please let me know.

I am hesitant to upgrade firefox because last time I did that it was continually crashing.  Therefore, I had to roll back from 3.1 to 3.0.8.

I would be happy to supply any additional information that someone might need to assist me with this issue.

Thanks in advance.

Jason

---

### Post by atyndall on 2009-06-05
[LIST=1]
[*]Login with sessions turned off as per normal.
[*]```
rm -rf ~/.cache/sessions
```
[*]Logout with sessions turned off.
[*]Log back in.
[/LIST]
It should be all fixed now.

Xfce4 has an issue with sessions for some reason. See [https://answers.launchpad.net/ubuntu/+source/xfce4/+question/71815](https://answers.launchpad.net/ubuntu/+source/xfce4/+question/71815) for more details.

---

### Post by tumescentliposuction on 2009-06-05
Hello...
          I think it might be problem with your xubuntu source because i have both and no problem with both of them....

---

