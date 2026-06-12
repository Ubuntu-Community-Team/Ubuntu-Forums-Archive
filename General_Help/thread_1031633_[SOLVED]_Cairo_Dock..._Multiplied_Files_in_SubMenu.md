---
title: "[SOLVED] Cairo Dock... Multiplied Files in SubMenu, when in current Folder is only 1 "
date: 2009-01-05
forum: General Help
---

### Post by sendblink23 on 2009-01-05
**SOLVED:** *Thanks to "chamber", Instead of placing a Folder at the dock, he suggested to use *Stack.*


Hi there, I'm running Ubuntu 8.10

I got a Cairo Dock issue... is it normal.. that certain folders you add, it appears files like multiplied inside of it (in the sub menu).. and in the actual Folder you only have the file 1 time only?? look at my Print Screen you will see 1 file I have.. it appears 4 Times multiplied in the submenu (I only have that file 1 time in the actual Folder)

Print Screen: [http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png](http://i29.photobucket.com/albums/c272/sendblink23/strangeCairoissueFolders.png)

Any way to fix this issue.. or is it normally like that?

---

### Post by sendblink23 on 2009-01-05
bump

---

### Post by sendblink23 on 2009-01-05
I'm guessing nobody uses Cairo Dock...   nobody has even replied after 4 hours since posted...

If you are using it.. Please at least WRITE that you do not have the same issue as mines.. just for me to know.. to keep a mind of hope.. of this Dock

I even had it posted at General Help nobody even answered anything related to my issue  (so removed it.. and Placed it here)

...  I'll give it..  2 days more...  if nobody tries to help..

Then I'll remove Cairo Dock then.

---

### Post by sendblink23 on 2009-01-06
bump

---

### Post by fabounet on 2009-01-06
> nobody has even replied after 4 hours since posted
ow, sorry , we are really useless volunteers, not even being able to help everybody on every forums on this planet in less than 4 hours...
we should be burnt I think.

and by the way, if you're hoping to run a Linux (or any else) environnement without any bug, please take the blue pill.

---

### Post by chamber on 2009-01-06
Have you tried using a different view for the sub menus?

That way you could confirm if the problem was the dock or just the sub menu.

---

### Post by sendblink23 on 2009-01-06
The problem is inside the Submenu Only .. And it also happens on all *different Views for the submenus.


> **chamber said:**
> Have you tried using a different view for the sub menus?

That way you could confirm if the problem was the dock or just the sub menu.

---

### Post by sendblink23 on 2009-01-06
I do not know if you read the part that where I said.. I had the Thread in the "General Help" ... it was there for more than 1 day & a couple of hours..  and nobody ever replied, so yesterday I decided to erase that other thread.. and instead...  having it here on "Desktop Effects & Customization" .. comprende .. I'm just asking if anybody has seen that error happening to them (People who have Cairo Dock) Thats all, and if they know how to fix it.. well cool, then help me out.. but do not Reply if you do not have a normal simple answer to any of the Both..

Like saying..


Oh yes I do have Cairo Dock, but no sorry I havent encountered an issue like yours.

> **fabounet said:**
> ow, sorry , we are really useless volunteers, not even being able to help everybody on every forums on this planet in less than 4 hours...
we should be burnt I think.

and by the way, if you're hoping to run a Linux (or any else) environnement without any bug, please take the blue pill.

---

### Post by chamber on 2009-01-06
In answer to your questions I could see the image but you hadn’t mentioned if you had tried all the different submenus, such as parabolic and carousel, I have cairo dock but the only applet in it that I have need of a sub dock for is the stacks applet using the parabolic view.

Mine does not show several at once.  

In my opinion you could use the stacks applet thats avaialable in the configure dock menu and put the file into it, its very handy to have I keep several fles or folders that I regularly access in it. Or you re install the dock and see if the problem happens again.

Im not at my desktop at the minute so I cant really check things properly but at least that theres a couple of things to try.

---

### Post by sendblink23 on 2009-01-06
That recomendation you gave me of instead to use *STACK* was much better, thank you =)


> **chamber said:**
> In answer to your questions I could see the image but you hadn&#8217;t mentioned if you had tried all the different submenus, such as parabolic and carousel, I have cairo dock but the only applet in it that I have need of a sub dock for is the stacks applet using the parabolic view.

Mine does not show several at once.  

In my opinion you could use the stacks applet thats avaialable in the configure dock menu and put the file into it, its very handy to have I keep several fles or folders that I regularly access in it. Or you re install the dock and see if the problem happens again.

Im not at my desktop at the minute so I cant really check things properly but at least that theres a couple of things to try.

---

### Post by chamber on 2009-01-06
Glad to have helped.

---

### Post by Favux on 2009-01-06
Hi sendblink23,

I know you were frustrated when you moved your post to this thread.  But fabounet is the cairo-dock project manager.  He was the help you were looking for.  You might want to review your first few posts before he posted.  Just a thought.

---

### Post by sendblink23 on 2009-01-06
Thanx for that Info, I did not know about that... at least he being the project manager...  He could at least point me with a Reply of any help.. in which he didn't really provide anything (although of mentioning of anybody not being able to help out... through 4 hours -with a proud Reply)  but simply saying at the end *A Matrix Related Quote*

Awesome he is the project manager..  it could have been good at least if he would have helped out during that moment, he was offline... when Chancer was helping me(in other words I didn't get a chance to manage on recieving help from fabounet, he replied many hours before I were online)

Thanx anyways, good to know that very important info. 

> **Favux said:**
> Hi sendblink23,

I know you were frustrated when you moved your post to this thread.  But fabounet is the cairo-dock project manager.  He was the help you were looking for.  You might want to review your first few posts before he posted.  Just a thought.

---

### Post by fabounet on 2009-01-07
if you didn't understand why I was so cynical, you should consider reading some other posts demanding help.
we don't spend our life on ubuntuforum or any other forum, nor we read all the topics. you seem to think it's normal to get a reply (and more, an answer !) just after you post a message here, do you think you are on an hotline site ?
and your way to complain so strongly about a bug was quite irritating.
I would suggest you to be more humble in the future, but of course, you can follow your way.
anyway I'll try to see if I can reproduce the bug at home, and if I can fix it.

---

### Post by fabounet on 2009-01-08
ok, it's fixed on the SVN.
a little bug in GVFS that sends a "created" event on an already existing file, hence the duplication.
thanks for your bug reporting ;-)

---

### Post by sendblink23 on 2009-01-08
> **fabounet said:**
> ok, it's fixed on the SVN.
a little bug in GVFS that sends a "created" event on an already existing file, hence the duplication.
thanks for your bug reporting ;-)

Thanx, and I'm completely sorry & I apologize for everything I said before.

If anything else.. I'll let you know.

---

