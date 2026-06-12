---
title: "Gnome-do microblogging plugin"
date: 2009-06-14
forum: General Help
---

### Post by toadliy on 2009-06-14
It seems that as of yesterday, the microblogging plugin for Gnome-do has stopped working properly... at least for me. When I try to post a tweet, an error message pops up that reads "Failed to post "xyz" to Twitter", "xyz" being the text of the tweet I want to post. However, when I go to my Twitter homepage, the tweet has in fact been posted, despite the error message from Gnome-do. However, if I try to reply to someone else's tweet, the third tab simply says "No results for:" and the drop-down menu is empty.

Is this a Twitpocalypse-related issue? Do I just have to wait for the next release of the plugin for this to be resolved, or is there a fix for this? In the meantime, any recommendations for other tweet notification/posting widgets/apps/etc.?

---

### Post by fcuk112 on 2009-06-16
i am having the same issue here, when i try to post a tweet it says "failed to post" but it has in fact worked.

how are you trying to reply to people?  i didn't know you could do that using gnome-do?

cheers.

---

### Post by toadliy on 2009-06-16
After you've typed in your message and selected "post to Twitter", you can tab over another time and it will open a third panel, where you can either search through a drop-down menu of recent posts in your feed, or type in the name of whomever you want to reply to. Of course, that doesn't work anymore...

---

### Post by ellaguno on 2009-06-18
This is happening to me too. I would add that previously I could read updates from twitter posts through the notification system but now it's also not working.

---

### Post by Karl S. on 2009-06-18
Having the same problem. I ran gnome-do with the terminal and tried posting a tweet. I got the failure notification, but it still appeared on twitter. The terminal said:
[INDENT][Error 13:14:22.761] Unable to post tweet. Check your login settings. If you are behind a proxy make sure that the settings in /system/http_proxy are correct[/INDENT]
I'm not behind a proxy. I'm guessing the "login settings" are my settings on twitter, but there's nothing strange there that I can see.

I think I found a possible fix [here]("https://bugs.launchpad.net/do-plugins/+bug/387525").

Brilliant. So far it works. Go to Synaptic, go to Software Sources, pre-released updates, close, look for gnome-do, update gnome-do plugins, go to .local/share/gnome-do and delete (or move) your plugins directory, open gnome-do, enable the microblogging plugin again, and you should be good to go.

---

### Post by toadliy on 2009-06-19
I think you mean ~/.local/share/gnome-do

But yes, this fix works brilliantly. Thanks!

---

### Post by jonny_boy27 on 2009-06-23
I can also confirm that the update in jaunty-proposed does indeed work

thanks :)

---

