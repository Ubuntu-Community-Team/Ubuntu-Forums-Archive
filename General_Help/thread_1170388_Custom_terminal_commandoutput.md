---
title: "Custom terminal command/output?"
date: 2009-05-26
forum: General Help
---

### Post by mike0020 on 2009-05-26
Is there a way I can have a custom terminal command, like 'music' and have the output be a custom output based off of the music playing in Rhythmbox? For example, when entering 'music' in terminal, I'd like for it to output something like "You're listening to [title] by [artist] from the album [album]"

I already know of the command 'rhythmbox-client --print-playing', however I'd like something with the output above. Thanks.

---

### Post by pro003 on 2009-05-26
there are a loads of screenlets which tells you what you're playin' ;)

---

### Post by Tibuda on 2009-05-26
You need to learn about bash aliases. See this thread: [http://ubuntuforums.org/showthread.php?t=1165172](http://ubuntuforums.org/showthread.php?t=1165172)

---

### Post by Boondoklife on 2009-05-26
> **mike0020 said:**
> Is there a way I can have a custom terminal command, like 'music' and have the output be a custom output based off of the music playing in Rhythmbox? For example, when entering 'music' in terminal, I'd like for it to output something like "You're listening to [title] by [artist] from the album [album]"

I already know of the command 'rhythmbox-client --print-playing', however I'd like something with the output above. Thanks.
```

rhythmbox-client --print-playing-format "You are listening to %tt by %aa from the album %at"
```

This sould do what ya want, just throw it in a bash script and mark it executeable.

---

### Post by Kareeser on 2009-05-26
Why script it? You can use the above code and put it into ~/.bash_aliases to the same effect :)

---

### Post by Boondoklife on 2009-05-26
> **Kareeser said:**
> Why script it? You can use the above code and put it into ~/.bash_aliases to the same effect :)

True, but I tend to just make scripts as I keep them all in a custom command folder. This way if I need them on another box, or need to reinstall, I just copy the files back and the commands are back.

Really just a personal preference thing :D

---

### Post by Tibuda on 2009-05-26
> **maletek said:**
> True, but I tend to just make scripts as I keep them all in a custom command folder. This way if I need them on another box, or need to reinstall, I just copy the files back and the commands are back.

Really just a personal preference thing :D

Or just copy the .bashrc file and the commands are back.

---

### Post by Boondoklife on 2009-05-26
> **danielrmt said:**
> Or just copy the .bashrc file and the commands are back.

One could do this, but say something got foobar'd in your config then you would have to hunt it down and fix it etc. this way there is not a chance of that. but as noted ether solution is fine.

---

### Post by mike0020 on 2009-05-26
Thanks everyone for your help, this is exactly what I was looking for :)

---

