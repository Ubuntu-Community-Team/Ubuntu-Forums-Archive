---
title: "Host key verification failed"
date: 2009-05-09
forum: General Help
---

### Post by rreyes1316 on 2009-05-09
I had to reinstall my iphone a re-jailbreak it. Before reconnecting I changed the default password for open SSH. When I attemtp to connect under "Connect to server" I get "Host key verification failed" message. How can I fix this?

---

### Post by Triptol on 2009-05-09
If I understand your question correctly, you can move the offending line:
```
nano ~/.ssh/known_hosts
```
Look for the line that you see when you connect to your iPod.

---

### Post by rreyes1316 on 2009-05-09
Aside from usint the :connect to server" I also tried the terminal. I entered iphone-mount and all I get is the following:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
99:cf:c6:ff:d3:6b:a0:d9:00:57:8a:76:d1:b2:2e:9e.
Please contact your system administrator.
Add correct host key in /home/rreyes3000/.ssh/known_hosts to get rid of this message.
Offending key in /home/rreyes3000/.ssh/known_hosts:2
RSA host key for 192.168.1.101 has changed and you have requested strict checking.
Host key verification failed.
read: Connection reset by peer

I entered the line suggested and I get the following:

|1|CSI5McoCcrDOjAzkMZSbmiOmHME=|DDZ67WTDN02WyAjyxrPr0I80KpA= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAwxTtBJ4fqHG7Ze0rENWxFPR9R2/IiOuEzj5I/i9M69Kv2eBqx57nce9aDTQBubmG+kuFylL7eoIos3x+D5+Ui/v8HOYJ6F/mn0H5dP4pYZeePLSXS/Mvl83tqNwKVNFStyLwwfmG8bYs4Um3phU14U/NTSlBiREbgNUOfoxfq0+iUuVTzZDl848HqDJwNaP$
|1|oNJn+EIUxnWjxAA/UJyLzEdicbY=|nW8jFo6s9TOFp4F1/6HkLTq9BEg= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxOy32h/XP6ibYWZPqF2sTVGRwv0H3Y5ocEb+QzVIpb2ABrja/aQGFkTyVTK60WOnJbnkBBGHSk9n8IfnsaZ8YXNaM1jSNmCyPOl6jlbz7NNDMaKEqSfhDDyUT58pmoYU4Wdd3nyB7Rgi5/eJcKbJJt1/Loh1p/q5DZVNVyeakG+VMCmCLg80wwDT5J/x4qb$
|1|N5sF3Q3b+OQDoVEg/R/73v/nmYE=|TTKpXRmYJcsE2OZqrZlU0yw0lO0= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxOy32h/XP6ibYWZPqF2sTVGRwv0H3Y5ocEb+QzVIpb2ABrja/aQGFkTyVTK60WOnJbnkBBGHSk9n8IfnsaZ8YXNaM1jSNmCyPOl6jlbz7NNDMaKEqSfhDDyUT58pmoYU4Wdd3nyB7Rgi5/eJcKbJJt1/Loh1p/q5DZVNVyeakG+VMCmCLg80wwDT5J/x4qb$

I am not sure what to do here.

To give you an idea of what I have doine I have included the links from which I followed. Everything was working fine before but since I had to restore my phone and jailbreak it again it stopped mounting. I am not sure if it is due to the new password I placed in openSSH on my iphone. Thinking that was it I reverted back to the old password "alpine" but that did not work either.

[http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux](http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux)

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Triptol on 2009-05-10
So what happens with SSH. As soon as you make a connection with an SSH Server (your iPod in this case), the SSH server (your iPod) sends its public key. 

Your SSH client will then ask you whether you want to accept this key and you have said "yes" to that question in the past. As soon as you say "yes" the public key of the SSH Server (your iPod) is stored in ~/.ssh/known_hosts.

This is a security feature. The next time when you connect to the same host, SSH compares the received SSH key with the stored one and complains if they are not the same (to make sure you are not somehow connecting to another computer).

So far so good.

And now you come along and reinstall SSH on your iPod (new jailbreak). At that moment a new public key was generated for your SSH Server (your iPod). So you reconnect and SSH complains that you are trying to connect to some SSH Server which now seems to have a new key. 

If you have a look at the error it says that line 2 is in error. Since you know this is an expected situation (you did a new jailbreak, so you have a new SSH key) you can just delete that line from the ~/.ssh/known_hosts file.

In short: delete the line and reconnect. You will be asked to confirm the new key and everything is happy beans.

---

### Post by rreyes1316 on 2009-05-10
Best explanation. I have posted this issue in other places and forums and have recveived vague and uncertain answers. Thanks. But how do i delete that file? I done konw all the commands and methods available to me. I am still a newbie to ubuntu--3.5 week old :)

---

### Post by albinootje on 2009-05-10
> **rreyes1316 said:**
> But how do i delete that file? 

Okay. Delete -line- nr.2 in that file.
After "gedit .ssh/known_hosts" it would be the second line that starts with "|1|". Remove that whole line till the start of the next "|1|".

---

### Post by Francewhoa on 2009-06-26
Same here. I found a solution on this post: [http://ubuntuforums.org/showpost.php...9&postcount=10]("http://ubuntuforums.org/showpost.php?p=7521619&postcount=10")

---

### Post by linuxfan86 on 2009-07-19
> **albinootje said:**
> Okay. Delete -line- nr.2 in that file.
After "gedit .ssh/known_hosts" it would be the second line that starts with "|1|". Remove that whole line till the start of the next "|1|".

omgoodness thank you so much for posting this!!! I deleted the second line as you said and I was able to ssh into my newly jailbroken and unlocked iphone 3G restored-upgraded to the new 3.0 firmware! :) :)

---

