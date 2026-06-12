---
title: "What does this mean?"
date: 2009-02-06
forum: General Help
---

### Post by Tews on 2009-02-06
I encountered this error while downloading a .deb package that i've never seen before ..

<code> /tmp/ubuntu-tweak_0.4.4-1~intrepid1_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.</code>

Does anyone know what I need to do to fix this??

Thanks

---

### Post by brian_p on 2009-02-06
> **Tews said:**
> 

Does anyone know what I need to do to fix this??

Using firefox? Tick 'Save File'.

---

### Post by Tews on 2009-02-06
Saving the file is not the problem ... *opening* the file is ... any ideas?

---

### Post by drs305 on 2009-02-06
To open the file, right click and associate the file type (.deb) to open with *gdebi*.

---

### Post by brian_p on 2009-02-06
> **Tews said:**
> Saving the file is not the problem ... *opening* the file is ... any ideas?

So the problem was **after** it was downloaded not '**while** downloading'

If by 'open' you mean 'install':

```
dpkg -i <package>
```

---

### Post by Tews on 2009-02-06
I knew that it was something simple :lolflag:

Thanks to all!

---

### Post by hyper_ch on 2009-02-06
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

