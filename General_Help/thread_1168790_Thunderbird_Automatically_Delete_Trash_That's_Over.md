---
title: "Thunderbird: Automatically Delete Trash That's Over Two Weeks Old?"
date: 2009-05-24
forum: General Help
---

### Post by jlacroix on 2009-05-24
Gosh, I'm just full of questions today!

I use Thunderbird for my email, and I was wondering if there was an extension or hack to make it delete files in my trash that are over two weeks old. Does anyone know of a way?

---

### Post by DeMus on 2009-05-24
> **jlacroix said:**
> Gosh, I'm just full of questions today!

I use Thunderbird for my email, and I was wondering if there was an extension or hack to make it delete files in my trash that are over two weeks old. Does anyone know of a way?

Does it have to be 14 days or is it okay to delete trash when you exit the program?
In the account settings, tab Server settings, you find a checkbox which will delete trash mail when you exit the program.
I can't find something about 14 days, or whatever time you want to have.

---

### Post by jlacroix on 2009-05-24
> **DeMus said:**
> Does it have to be 14 days or is it okay to delete trash when you exit the program?
In the account settings, tab Server settings, you find a checkbox which will delete trash mail when you exit the program.
I can't find something about 14 days, or whatever time you want to have.

I couldn't find that option either. I'd prefer not to have the trash deleted when I exit, because I usually end up needing something.

---

### Post by jlacroix on 2009-06-01
Is this not possible? :(

---

### Post by Irihapeti on 2009-06-02
I've done the following with other folders but not with the trash, but I see no reason why it shouldn't work there as well.

Right click on Deleted in the list of folders, choose Properties from the popup menu (last on list) then the Retention Policy tab. Uncheck the Use server defaults option. You can then edit the default 30 days retention option to 14 days or any figure you like.

Just don't accidentally move a message there that's over 14 days old, or it will be toast :( .

---

### Post by jlacroix on 2009-06-02
> **Irihapeti said:**
> I've done the following with other folders but not with the trash, but I see no reason why it shouldn't work there as well.

Right click on Deleted in the list of folders, choose Properties from the popup menu (last on list) then the Retention Policy tab. Uncheck the Use server defaults option. You can then edit the default 30 days retention option to 14 days or any figure you like.

Just don't accidentally move a message there that's over 14 days old, or it will be toast :( .

I tried that, but it didn't work. :(

---

### Post by akakingess on 2009-06-02
Have you tried creating a filter, I know I can choose to go in and say that if a message is x days old then "delete message', now i am not quite sure whether that would work if message is already in the trash but i couldn't see why not, or maybe set up a filter to send messages that old to a certain folder that you create and then after 14 days move to trash and choose the empty deleted items upon closing of Thunderbird.  Hope this helps, that's all I could come up with.

akakingess

---

### Post by Irihapeti on 2009-06-02
> **jlacroix said:**
> I tried that, but it didn't work. :(

I just tested it on my own installation to be sure, and it's definitely working.

There are two things I can think of. One, that I'm using the "official" Thunderbird downloaded from Mozilla, and you may be using the version from the Kubuntu repositories. Sometimes there are differences between the "official" and "(K)ubuntu" versions of the same program.

The other is that I didn't explain it very well, so I've included a couple of screenshots which might make the process a bit clearer. The first one shows the popup menu - use the "properties" option at the bottom, and the second shows the retention policy tab set up to delete messages over 14 days old.

HTH

---

### Post by jlacroix on 2009-06-03
> **Irihapeti said:**
> I just tested it on my own installation to be sure, and it's definitely working.

There are two things I can think of. One, that I'm using the "official" Thunderbird downloaded from Mozilla, and you may be using the version from the Kubuntu repositories. Sometimes there are differences between the "official" and "(K)ubuntu" versions of the same program.

The other is that I didn't explain it very well, so I've included a couple of screenshots which might make the process a bit clearer. The first one shows the popup menu - use the "properties" option at the bottom, and the second shows the retention policy tab set up to delete messages over 14 days old.

HTH

Well, I did that as you suggested, and the messages that were over 14 days old didn't go anywhere. Then, I made a mistake and I accidentally emptied my trash completely. So now, (unfortunately) I have no way to test it anymore. I really appreciate your help, but I guess I'm forced to wait for two weeks to see if it starts working. :(

---

### Post by akakingess on 2009-06-03
Does the filter method not work under kubuntu? I am on Ubuntu and a noobie at that, but I tried it on my Thunderbird and I figured I could move anything over 14 days old to the trash and then select it to empty the trash upon exit. I was just wondering if you had tried it or am I in over my head?

akakingess

---

### Post by jlacroix on 2009-06-03
I haven't had a chance to try it, my entire trash folder got emptied and I have nothing to delete over 14 days old.

---

### Post by akakingess on 2009-06-03
> **jlacroix said:**
> I haven't had a chance to try it, my entire trash folder got emptied and I have nothing to delete over 14 days old.
Just a suggestion when you get the chance, I would create a subfolder under your inbox and have a filter that sends emails 7 days or older to that subfolder, then create a filter on that subfolder that would send anything over 14 days old to the trash. Then choose to empty trash upon exit. I only suggest it that way so that it is kind of a two-tiered safety measure to keep from accidentally deleting an email that you needed to refer to 12 days after you got it.  I hope it all works out for you, whichever way you can do it.

akakingess

---

