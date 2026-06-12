---
title: "Gmail webapp not being tracked by Unity"
date: 2013-10-18
forum: Desktop Environments
---

### Post by Zunino on 2013-10-18
Hello.

I have installed (i.e. accepted the webapp installation prompts within Firefox) both Gmail and Twitter as Unity webapps, so that I can launch them directly from the side panel. One thing has me puzzled though: when I launch Twitter, it behaves similar to a regular application (except for the fact that it also causes a browser instance to be launched). Unity seems to track its execution, showing indicators (those little arrows) on both sides of the Twitter app icon. This, however, is not the case with the Gmail launcher. Clicking on it causes the browser to be opened and taken to the Gmail page, but there are no indicators on the Gmail icon, as if it served as a mere link and nothing else.

Is there a way to make the Gmail Unity webapp behave the same way Twitter's does? I have checked the .desktop files for both launchers but found nothing of relevance. Just in case, I'm posting their contents below.
```
[Desktop Entry]
Name=Twitter
Type=Application
Icon=unity-webapps-twitter
MimeType=
Actions=S0;S1;S2;S3;S4;S5;S6;S7;S8;S9;S10;
Exec=unity-webapps-runner -n 'VHdpdHRlcg==' -d 'twitter.com' %u
StartupWMClass=Twittertwittercom
``````
[Desktop Entry]
Name=GMail
Type=Application
Icon=unity-webapps-gmail
MimeType=
Actions=S0;S1;S2;S3;S4;S5;S6;S7;S8;S9;S10;
Exec=unity-webapps-runner -n 'R01haWw=' -d 'mail.google.com' %u
StartupWMClass=GMailmailgooglecom
```Thank you in advance for any tips.

---

### Post by gcidgarcia on 2013-10-19
It happens to me also. With Facebook it is ok, it  integrates with Unity, the icon on it being a link to Facebook tab in  the browser. I can also see Facebook in the  messaging menu and I'm notified everytime I get a message or  notification, just like an incoming email on Thunderbird (mail envelope turns blue). The problem's  with Gmail (whose webapp was supposed to do it also). It is not working  at all, despite for an icon in Unity that only opens Gmail on a new  Firefox window.

I guess webapps are still buggy on 13.10 or is there a way around?

Thanks in advance.

---

### Post by JonPaul on 2013-10-20
This problem started in 13.04 with an update. The gmail webapp does not indicate the number of messages, nor does it show in indicator messages, nor does it go to an already open gmail tab. Rather it opens a new instance of firefox every time. Google calendar webapp on the other hand works exactly as expected. I am currently using gmail-indicator instead which does change the message envelope and gives notifications but also does not switch to the open tab....

see [http://ubuntuforums.org/showthread.php?t=2158939&highlight=gmail+indicator](http://ubuntuforums.org/showthread.php?t=2158939&highlight=gmail+indicator)

---

### Post by gcidgarcia on 2013-10-20
That's good to know there's nothing wrong with the system itself. I wonder if Unity Mail does the trick and it's a good option. Which would be more reliable and recommended to patch the webapps bugs so far, gmail-notifier or Unity Mail?

---

