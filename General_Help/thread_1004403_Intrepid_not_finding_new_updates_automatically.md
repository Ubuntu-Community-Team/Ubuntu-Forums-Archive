---
title: "Intrepid not finding new updates automatically??"
date: 2008-12-07
forum: General Help
---

### Post by TWO on 2008-12-07
Hello

Since I've been using Ubuntu Intrepid (32-bit), it hasn't once informed when there are new updates.

I have the update manager set to check for updates regularly and yet the only time I ever seem to get an update notification is if I happen to run ```
$ apt-get update
``` in the terminal, if I happen to have added a new repository or something.

Has anyone else been experiencing/experienced this problem and if so, does anyone have any ideas on how to fix it?

Thanks in advance

TWO

---

### Post by DougieFresh4U on 2008-12-07
Just a thought, have you checked 'System>Administration>Software Sources'
Then look at the 'Updates' tab and see what Automatic Updates is set to.

---

### Post by TWO on 2008-12-08
> **DougieFresh4U said:**
> Just a thought, have you checked 'System>Administration>Software Sources'
Then look at the 'Updates' tab and see what Automatic Updates is set to.

Yeah, that's one of the first things I checked, and it is set to 'Daily.'

That's why I'm finding this problem rather unusual...

TWO

---

### Post by SoDanishWasLike on 2008-12-08
Wow thats reaally crazy

I'm def. keeping an eye on this thread to see what the answer will be!

---

### Post by frankleeee on 2008-12-09
I assume that all of the third party repositories are ticked on along with any other you might want, that the CD is ticked off, and that in the apt list none of the repositories have a # at the front of the repo. You also might look for the apt-source lists available on line to make sure yours is up to date. Also if you run the update manager or terminal or reload from synaptic do any errors show.

---

### Post by TWO on 2008-12-13
As you can see from the attachments, I have my updates set to daily in Synaptic Package manager and yet when I open the update manager, you can clearly see that the packages haven't been updated for 4 days. 

I leave my laptop on for several days at a time and yet I am never receive an update notification....

My ```
/etc/apt/sources.list
``` file also looks OK, with nothing unusual being marked with '#'.

I am completely baffled by this!!

TWO

Edit: Just compared to the list given on [http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid) and nothing in mine appears unusual too...

---

### Post by zerohero on 2008-12-14
I have the same problem, and found that /etc/cron.daily/apt did not have execute-permission. I believe that this script is responsible for update-manager checking the sources.

So i suggest checking if the you have the execute-permission set, and if not, set it (sudo chmod a+x /etc/cron.daily/apt)

---

### Post by TWO on 2008-12-14
> **zerohero said:**
> I have the same problem, and found that /etc/cron.daily/apt did not have execute-permission. I believe that this script is responsible for update-manager checking the sources.

So i suggest checking if the you have the execute-permission set, and if not, set it (sudo chmod a+x /etc/cron.daily/apt)

So this would mean that it is a bug then? What is the reason for the missing execute permission?

---

### Post by ethos_dacapo on 2008-12-23
Can i get confirmation from anyone that this is the appropriate fix?

---

### Post by TWO on 2008-12-24
> **zerohero said:**
> I have the same problem, and found that /etc/cron.daily/apt did not have execute-permission. I believe that this script is responsible for update-manager checking the sources.

So i suggest checking if the you have the execute-permission set, and if not, set it (sudo chmod a+x /etc/cron.daily/apt)

Well, I can confirm that the /etc/cron.daily/apt file was indeed not given execute-permission and so I have made it so. 

(Again I say, surely that file not having an execute-permission is a bug?)

Now I'll just need to wait for some updates to come through and then we can confirm.

---

### Post by outcesticide on 2008-12-24
well this might help im not sure but if you go into synaptic and click settings and hit the updates tab you can configure to how you like it. theres 3 categories(ubuntu updates, automatic updates, and release upgrade)

hope that helps:)

---

### Post by outcesticide on 2008-12-24
oh nvm i see you already did that sorry :(

---

### Post by TWO on 2008-12-24
> **outcesticide said:**
> oh nvm i see you already did that sorry :(

Hehe, thanks anyway though. It was one of the first things I checked! I'm trying zerohero's suggestion. So far, the apt file not having execute-permission I've found to be true, so maybe we'll soon see if we have found the solution...

---

### Post by 73ckn797 on 2008-12-24
> **TWO said:**
> Hello

Since I've been using Ubuntu Intrepid (32-bit), it hasn't once informed when there are new updates.

I have the update manager set to check for updates regularly and yet the only time I ever seem to get an update notification is if I happen to run ```
$ apt-get update
``` in the terminal, if I happen to have added a new repository or something.

Has anyone else been experiencing/experienced this problem and if so, does anyone have any ideas on how to fix it?

Thanks in advance

TWO


I never get notifications of updates with auto update turned on. It will only tell me that updates were applied within what ever time frame there is between when it was updated and when I make the inquiry to check for updates at System/Update Manager. I have mine setup to notify of available updates at this time and am not experiencing the same issue. I really am probably no help but if mine or anyone elses comments help keep you on track through your diagnosis of the problem, well, that is still helpful!!

---

### Post by ethos_dacapo on 2008-12-24
[http://ubuntuforums.org/showthread.php?p=6418073#post6418073]("http://ubuntuforums.org/showthread.php?p=6418073#post6418073")

gave me confirmation earlier today...
I applied the 755 permissions so we'll see come tomorrow.

---

### Post by ethos_dacapo on 2008-12-25
> **zerohero said:**
> I have the same problem, and found that /etc/cron.daily/apt did not have execute-permission. I believe that this script is responsible for update-manager checking the sources.

So i suggest checking if the you have the execute-permission set, and if not, set it (sudo chmod a+x /etc/cron.daily/apt)

worked for me

---

