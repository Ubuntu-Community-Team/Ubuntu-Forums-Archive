---
title: "System testing ASLEEP!"
date: 2010-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by itsols on 2010-07-07
I was curious to see if everything was in good shape. So like I used to in the past, I started System testing. Then I waited, and waited and waited.... After more than 3 minutes, the progress bar kept moving from side to side that only reminded me of the old KITT - lol...

I used system monitor that indicated that the CHECKBOX program (i.e., system testing) was 'sleeping'... I tried killing the process. It does NOT show in the process list but it is still on the screen - yes, even as I type this post.

Any ideas please...

---

### Post by mikewhatever on 2010-07-07
Interesting, what's the output of
```
ps -e | grep checkbox
```
?

---

### Post by itsols on 2010-07-07
Wow!!! I can't grep it as I can't repeat the issue. But now that I rerun the system test utility, it works even more differently than before...

Ok, first the good news... Some tests worked. Some tests I skipped. For example, I skipped the internal microphone test (as I don't have one) and the thumb scanner...

Now the issues.

1. It did not perform the dead pixel test. I was expecting a single-coloured screen in red, green and blue. But this never happened. Waited... but nothing. So I skipped it.

2. On the keyboard test, I was expecting a text area to appear when I clicked on the TEST button. It never came up. Thinking I did something wrong, I went BACK and retried the keyboard test. SAME...

3. Finally, it came to the part of viewing the report prior to submission to launchpad. Then I was bombarded with the following message in the browser:
SEE ATTACHMENT PLEASE.

I really hope a new stable release comes out soon!

Advice to other users: DON'T UPGRADE TO VERSION 10.04, no matter how cute it looks... lol

---

### Post by johnmay on 2010-12-26
I realise that the thread is a bit old, however I am currently experiencing the same problem with 10.10. my searching does not provide the process name that I should look for to end/stop/kill the process of System Testing. 

Any ideas?

maybenot@Optimus-Prime:~$ ps -e | grep checkbox
22057 ?        00:00:00 checkbox-gtk


Thanks!

---

### Post by johnmay on 2010-12-26
Posting because thread not showing up in new posts thread...

---

### Post by mybodya on 2011-03-25
I have the same thing, man. I can't kill the process

---

### Post by littlepear on 2011-08-27
Same problem occuring here:
00:00:00 checkbox-gtk


Is anyone using two-seat version of Userful Multiplier over their Edubuntu?

:popcorn: (waits patiently)

---

### Post by itsols on 2011-08-28
I'm surprised at your timing :)

Actually I don't even remember this issue - lol...

Perhaps one of the updates did the trick. Have you folks installed the regular updates/patches? If you're a regular Ubuntu user, you should know that you have an update at least once a week.

Just curiously I tried sys testing and it works just fine.

In any case, I'd advise going in for the newer version 11.04 if you have what it takes (resources, time and patience). I'm quite happy with 10.10 now I'm compelled to upgrade by April - that's when 10.10 reaches its end of life cycle for support/upgrades. I really hate the time of an upgrade because of the many software/tool configurations I must make but it's something inevitable. Too bad we don't have an LTS around the corner.

---

