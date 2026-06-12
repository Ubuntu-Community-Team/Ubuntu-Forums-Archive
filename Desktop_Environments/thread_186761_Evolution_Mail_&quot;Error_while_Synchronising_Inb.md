---
title: "Evolution Mail: &quot;Error while Synchronising Inbox&quot;"
date: 2006-06-02
forum: Desktop Environments
---

### Post by samir85 on 2006-06-02
Hi,

I'm using Evolution Mail to get my mails from a POP server.

For a while it worked fine, but then I always got this error when synchronizing the the POP server:
```
Error while Synchronising Inbox
Summary and Folder mismatch even after sync
```
And all messages I get, are displayed twice in my inbox !

After deleting all *summary files in ~/.evolution/mail/local, the problem is solved for some time, but then after a few I start getting those errors again !

---

### Post by rune_kg on 2006-06-19
Yes I know

Exact same thing happens to me. It started when I Changed a filterrule at the same time that I checked my mail. My mistake:)

Rune

---

### Post by tom-ubuntu on 2007-01-09
> **samir85 said:**
> Hi,

I'm using Evolution Mail to get my mails from a POP server.

For a while it worked fine, but then I always got this error when synchronizing the the POP server:
```
Error while Synchronising Inbox
Summary and Folder mismatch even after sync
```
And all messages I get, are displayed twice in my inbox !

After deleting all *summary files in ~/.evolution/mail/local, the problem is solved for some time, but then after a few I start getting those errors again !
Got now the exact same problem again. Did you find a solution? I can't get it to work ](*,) 

I really hope, this get fixed or improved. So far, I could fix the problem. But not this time....

Thanks for any advice!

---

### Post by tom-ubuntu on 2007-01-11
Got it fixed with the work around mentioned here:

[https://bugs.launchpad.net/evolution/+bug/27014](https://bugs.launchpad.net/evolution/+bug/27014)

```


I know this is not the solution but it is a work around that works!

Please make sure you back up the relevan data file for the problem folder first, just in case.

Often when the mismatch message occurs evolution cannot generate a .ev-summary file, especially with large (500+ Meg) files.

To overcome the problem for folder FOO

Make a new folder FOO1

go to FOO and select all emails

Move all mails from FOO to FOO1

select FOO1 (the mismatch error will come up again as you leave FOO)

Check all the mails are there.

Quit and restart evolution to check the data is there, select FOO1. Then select another folder to make sure the error does not occur on this new file.

Delete FOO (you need to expunge it first)

Rename FOO1 to FOO

Everything should now work.

Finally, for good housekeeping check the ~/.evolution/mail/local/Inbox.sbd/....... directory to see that the new files are all listed as FOO.

This does not always happen (some will retain the FOO1 element) and it will not cause a problem but will be confusing if you regularly check the evolution directory and file structure so;

Instead of renaming FOO1 to FOO

Stop then restart evolution

Make a new folder FOO

Move the files from FOO1 to FOO

Stop start and check once more

Delete FOO1

Hope this of use to beleaguered evo users

```

---

### Post by Cornbreadly on 2007-01-20
I am not completely sure I know what a "foo" folder is...

I looked around the evolution files and looked at the hidden ones.  Could I have more noob friendly directions on how to implement the above fix?

---

### Post by Kevanx on 2007-07-18
The above fix looks thorough, but this fix worked for me for this same problem (no idea what caused it).

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014/comments/6](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014/comments/6)

For n00bs - NOTE -USE ONLY AT YOUR OWN RISK!!! This might not apply to your problem, but it's relatively unrisky.
1. Close Evolution.
2. Open up your terminal (Applications > Accessories > Terminal) - are you tingly yet?
3. type
```

rm ~/.evolution/mail/local/Inbox.ev-sum*

```
and hit enter/return.

4. Open up evolution.

I'm a bit of a n00b too, but here is what you are doing:

rm is a terminal command for remove (makes sense, right?)

~ tells the terminal that you are looking in your home directory, which is where your preferences are kept, in the .evolution folder. Then it will look in the 'mail' folder, and finally, in the 'local' folder.

Once it gets there, it will delete any file that starts with 'Inbox.ev-sum'
This deletes two index files - Inbox.ev-summary and Inbox.ev-summary-meta
WHATEVER YOU DO, don't type that line with just 'Inbox' at the end, because that will delete your inbox. This will delete the indexes, which will be recreated as soon as you reopen Evolution.

These files are INDEX files of your Inbox folder, and somehow contribute to the weird error (and double messages) associated with this glitch. If you happen to have the same problem with Sent or another folder (although I haven't heard of this happening), you would do the same, except replacing Inbox.ev-sum* with Sent.ev-sum*

Hope this helps!

---

### Post by Buffaloed on 2007-09-23
> **Kevanx said:**
> The above fix looks thorough, but this fix worked for me for this same problem (no idea what caused it).

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014/comments/6](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014/comments/6)

For n00bs - NOTE -USE ONLY AT YOUR OWN RISK!!! This might not apply to your problem, but it's relatively unrisky.
1. Close Evolution.
2. Open up your terminal (Applications > Accessories > Terminal) - are you tingly yet?
3. type
```

rm ~/.evolution/mail/local/Inbox.ev-sum*

```
and hit enter/return.

4. Open up evolution.

I'm a bit of a n00b too, but here is what you are doing:

rm is a terminal command for remove (makes sense, right?)

~ tells the terminal that you are looking in your home directory, which is where your preferences are kept, in the .evolution folder. Then it will look in the 'mail' folder, and finally, in the 'local' folder.

Once it gets there, it will delete any file that starts with 'Inbox.ev-sum'
This deletes two index files - Inbox.ev-summary and Inbox.ev-summary-meta
WHATEVER YOU DO, don't type that line with just 'Inbox' at the end, because that will delete your inbox. This will delete the indexes, which will be recreated as soon as you reopen Evolution.

These files are INDEX files of your Inbox folder, and somehow contribute to the weird error (and double messages) associated with this glitch. If you happen to have the same problem with Sent or another folder (although I haven't heard of this happening), you would do the same, except replacing Inbox.ev-sum* with Sent.ev-sum*

Hope this helps!

Thanks for posting that. I ran into this problem today, Your solution worked perfectly.

---

### Post by nick4mony on 2008-01-01
> **Cornbreadly said:**
> I am not completely sure I know what a "foo" folder is...

I know it's rather late, but here goes.
*FOO* is simply an example of a folder name.  I have a problem with a folder called *Commercial* (emails from my ISP and other commercial people), so whenever I see *FOO* in the instructions, I replace it with *Commercial*.

---

### Post by reswob on 2008-02-03
The command line worked for me too.  Thanks.

---

