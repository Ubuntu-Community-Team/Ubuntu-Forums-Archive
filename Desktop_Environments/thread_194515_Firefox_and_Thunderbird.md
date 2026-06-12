---
title: "Firefox and Thunderbird"
date: 2006-06-11
forum: Desktop Environments
---

### Post by FCM on 2006-06-11
I have set Thunderbird as my default email system. When using Firefox and I try to send a link by email, Firefox does nothing. Is there a way to make Firefox use Thunderbird? I have browsed this forum and searched for the answer but it seems I must be the only one who can't figure this out ;) 

Thianks for your help.

---

### Post by art on 2006-06-11
Choose from System->Preferences->Preferred Applications, for browser Custom and the command firefox.ubuntu %s

---

### Post by arizonagroovejet on 2006-06-11
I'm not entirely sure from your wording, but I'm thinking you want to have Thunderbird launch when you click on a mailto: link in a webpage whilst using Firefox, right?

In Firefox type about:config in to the location field. Find a Preference called

network.protocol-handler.external.mailto

If it doesn't exist create it as type Boolean Set it's value set it to 

true



Then find

network.protocol-handler.app.mailto

If it isn't there (it probably isn't) create it as type string. Set it's value to

/usr/bin/mozilla-thunderbird

---

### Post by FCM on 2006-06-11
Thanks - the fix worked!

---

### Post by FCM on 2006-06-11
Arizonagroovejet!

WHOOPS! Now I have the opposite situation. When I click on a link in Thunderbird it opens up in Konqueror instead of Firefox. I tried to set the default web browser through the following steps: System Settings=>Kde Components but no change.
I tried through Thunderbird Preferences=> Advanced => configuration editor and tried to change the network protocol as described above but no success.
It could be I was trying to change the wrong items.  Can you help again, thanks.

---

### Post by arizonagroovejet on 2006-06-12
[QUOTE=FCM]Arizonagroovejet![/QUOTE]

Hello.

[QUOTE=FCM] When I click on a link in Thunderbird it opens up in Konqueror instead of Firefox. [/QUOTE]

OK, two ways to fix this -

1] System wide for all users and will affect applications other than Thunderbird -
```
$ sudo update-alternatives --set  x-www-browser /usr/bin/firefox 
```                
Thunderbird invokes the command x-www-browser to open an url in a web browser.  /usr/bin/x-www-browser is a symlink to /etc/alternatives/x-www-browser which is in turn a symlink to which every browser is considered to be the default for the system. In Kubuntu it points at /usr/bin/konqueror bu default and the above command changes it to point at Firefox. For more info look at the file /etc/alternatives/README

2] Only for your user and only affect Thunderbird.
Start Thunderbird and go to Edit > Preferences > Advanced  and click the 'Config Editor' button. Find the Preferences called network.protocol-handler.app.http and network.protocol-handler.app.https and alter their values to firefox.

---

### Post by FCM on 2006-06-12
Thanks - all is the way I want it now!

I had tried to change the protocol handler the way you described but somehow it didn't make the changes. This time it worked without a problem...Thanks again for your help!

---

### Post by morikaweb on 2006-08-29
I tried to do this for swiftfox in /opt/swiftfox/swiftfox but it keeps giving me a msg saying it can not find alternitive /opt/swiftfox/swiftfox. Any ideas?

---

### Post by krus on 2006-08-29
thank you thank you thank you thank you, arizonagroovejet.  

Having konquerer launch from thunderbird, despite having changed every concievable setting in KDE and thunderbird, was driving me nuts.

your july 12th update-alternatives clue made my day.

---

### Post by krus on 2006-08-29
> **morikaweb said:**
> I tried to do this for swiftfox in /opt/swiftfox/swiftfox but it keeps giving me a msg saying it can not find alternitive /opt/swiftfox/swiftfox. Any ideas?

Does /opt/swiftfox/swiftfox work if you call it directly? Is it executable? is it spelled right? (those are the sorts of goofy things I've been known to overlook...)

---

### Post by morikaweb on 2006-08-30
Yes its real and it runs. I even tried creating a symlink to /opt/swiftfox/swiftfox in /usr/bin/ but it still did not work when I pointed the x-www-browser to it. Nedless to say this is a bit annoying ](*,)

---

### Post by morikaweb on 2006-09-10
From the lack of replies I can only assume that no one has ever gotten this to work. If that's the case then ubuntu/kubuntu has some pretty major flaws to overcome.

---

