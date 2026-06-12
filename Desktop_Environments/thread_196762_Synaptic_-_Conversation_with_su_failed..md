---
title: "Synaptic - Conversation with su failed."
date: 2006-06-14
forum: Desktop Environments
---

### Post by ajgreeny on 2006-06-14
I've just updated my Dapper Kubuntu system this evening using synaptic.  Many of the kde packages were updated.  After doing this and then rebooting for a completely unrelated purpose I found that synaptic was refusing to start, the error message telling me that "Conversation wuth su failed" even though my password was correctly entered.

A quick search on the forums told me that I needed to add my name to the /etc/sudoers file in the format:-

username   ALL=(ALL) ALL

What caused this to happen?  I found it quite worrying and was so pleased to get it back having added that line to the sudoers file.
Also, why is it that the forum said that the sudoers file must be edited with visudo?  I tried this but couldn't make head or tail of visudo so did it using kate, and everything seems to be OK now.  Have I messed up something or should all be perfectly alright now?

---

### Post by dalee on 2006-06-14
Hi,

Yeah, you should be fine. Breaking Sudo has been known to happen. I just had to fix one of my boxes too:-x .

Here's a link to a pretty good explaination of how to fix it. [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

dalee

---

### Post by ajgreeny on 2006-06-15
Thanks, dalee.
All seemed to be OK but I was totally baffled by what happened, made even more puzzling by the fact that I could still use sudo and get into synaptic if I used a GNOME session instead of KDE, that's why I thought perhaps the updates of various KDE packages that I had just done may have affected things.  What is even more puzzling is the fact that after failing to get synaptic up and running, I could still start konqueror as root using "kdesu konqueror" as the command and edit the sudoers file with kate.  Wierd, eh?

I just happen to have another identical partition with (K)ubuntu on the same machine but a separate hard disk which I use to test out things that might just break the system (not expected from just updating of course, hence this thread), so I'll do the same update this morning on that setup and see what happens there.  I see, incidentally that the /etc/sudoers file on that partition does not have the line
username ALL=(ALL) ALL
in it as I appear to need in my main working setup, so things seem even more strange.

Oh well!  Here goes.  Lets see what happens on this other partition when I update.  I'll be back soon to let you know.

---

### Post by ajgreeny on 2006-06-15
Hi again.
It's now nearly an hour later after trying the update on my other drive/partition, and all went well there.

Just to test out the whole thing again, knowing now how to put it right if it all went wrong again, I reinstated the original /etc/sudoers file without the extra line
username ALL=(ALL) ALL
And guess what?  Everything still works as it should and did in the past.

Seems to me it must have just been a glitch in my system somewhere that upset sudo in some way.  Thanks for your reply about what I did and that all should be (and was) OK. If there are any further strange happenings in this saga, I'll be sure to let you know.

---

