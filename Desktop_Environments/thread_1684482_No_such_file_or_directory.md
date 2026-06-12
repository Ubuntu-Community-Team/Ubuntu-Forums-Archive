---
title: "No such file or directory"
date: 2011-02-09
forum: Desktop Environments
---

### Post by bluntz on 2011-02-09
An executable fails to be found and run when called
even though it is found and displayed by ls.
I am on lucid LTS fully updated 32 bit.
The file has permissions setup but any attempt to run it results in the error
bash ./executablename  No such file or directory


This situation also seems to be present in kcron
sometimes my scripts dont run from it even though
the run now option does.

This bug has been around since dapper it would be nice if someone could fix it.

---

### Post by mcduck on 2011-02-09
What happens if you try using the full path to the executable?

(*/the/full/path/to/executablefile* instead of *./executablefile*)

(since nobody else has noticed such an issue, it's not likely to be a bug, more like an error in the way you are trying to do things)

---

### Post by bluntz on 2011-02-10
> **mcduck said:**
> What happens if you try using the full path to the executable?

(*/the/full/path/to/executablefile* instead of *./executablefile*)

(since nobody else has noticed such an issue, it's not likely to be a bug, more like an error in the way you are trying to do things)

I am always amazed how anyone comments on a post that they do not read.
If you don't know the answer then don't comment.
Even a cursory examination of this BUG shows its been around for years.

---

### Post by mcduck on 2011-02-10
I *did* read your post, you didn't mention even trying to use full path, only trying to execute the file as if it was in your current directory.

And you didn't provide a link to any bug report, and I can't find one, not to mention ever even hearing of anybody having ran into such bug.

So, based on any information, and the fact that you dind't mention even trying using the full path, it still doesn't look like a bug. 

So try using the full path if you haven't done that already. If you *have* tried that, then say so instead of accusing me from not reading your post. :D If you know there's a bug report about such issue, then please provide a link to it (not that anybody in the forums could help you if there really was such a bug, in that case you should provide information to that bug report and wait for the developers to fix it)

---

### Post by bluntz on 2011-02-11
Now you say you read my post,
That you couldn't find or ever heard of this before?
If you actually did read the post you would have seen
that I said it 's been around for years  at least since dapper.
So am I a liar?
Do you think i Have I come here to waste my time?



<snip>

---

### Post by bluntz on 2011-02-12
The file exists (test)
> bluntz@bluntz-box:~/quake$ ls test -l
-rwxr-xr-x 1 bluntz disk 77196 2011-02-07 16:58 test

but can't be found
> bluntz@bluntz-box:~/quake$ ./test
bash: ./test: No such file or directory

not outside of the directory either
> bluntz@bluntz-box:~$ /home/bluntz/quake/test
bash: /home/bluntz/quake/test: No such file or directory


---

### Post by bluntz on 2011-02-27
>  not that anybody in the forums could help you if there really was such a bug

Why would you insult someone looking for help and tell them they are not doing it right if you never
had the skill or the intent of doing so?
This is Ubuntu's Idea of Tech support.Insult them and if they don't like it, edit their post delete their account ect...
Great job Team!

---

### Post by mcduck on 2011-03-02
Now, lets see:

I started by asking you a question, and suggesting that since nobody else is having such problem and there doesn't seem to be such bug reported for any of the Ubuntu versions , the problem might be in how you are doing things. If you consider suggesting the possibility that you might have made an error an insult, feel free to do so. It wasn't intended as an insult, though.  

After that you have insulted me in three posts, and took considerable amount of time before posting any relevant information about the problem you have, even though I asked if you have tried using the full path in the very first answer you got. A simple yes or no to that relevant question wouldn't have been a big deal before becoming aggressive, would it?

It doesn't seem to be a bug, since there's no bug report about such bug. If it nevertheless would be a bug you'd have to report it (and post a link to the report here to provide people trying to help you with the appropriate information), and being a bug it would be something the *developers* would have to address. Not something any volunteers on these forums could help you with.

That being said I leave you to think how to get volunteer help on Internet forums the correct way. Not having skills to help you and whatsoever. :D As a tip it works pretty much the same way you'd ask any of your friends or other people in real life to use their  time to help you. Ranting, accusations, insults or demands are not known to work very well...

---

### Post by bluntz on 2011-03-03
Well then stop trolling my thread

---

### Post by asmoore82 on 2011-03-03
To get meaningful help, you need to give more information.
What app are you really trying to run here?
Can I reproduce this same error on my Ubuntu machine?

A link to a bug report would also be nice.

I know that at least one reason that this cryptic error message can show up
is when you attempt to run a 32-bit app on a 64-bit OS and the relevant
32-bit library is not installed. Perhaps your situation is *vice versa*.
Have you downloaded a 64-bit binary blob on a 32-bit OS?

---

### Post by bluntz on 2011-03-04
From what little I can find about this
I suspect The same conflict with kernel.
I updated and built 2.6.35-23-generic.
I will try another kernel and test again,thank you.

---

### Post by bluntz on 2011-03-22
Spot on Asmoore82 !

Bin File was 64 just as you intuited.
Thank you.

---

