---
title: "Installing Matlab - some kind of Java error"
date: 2010-10-23
forum: Education &amp; Science
---

### Post by Kdar on 2010-10-23
I asked it in general support area, but it got moved down very quickly.

Maybe people who visit this part of forum can help me better.

Here is the link to my original post: [http://ubuntuforums.org/showthread.php?t=1603876](http://ubuntuforums.org/showthread.php?t=1603876)

When I try to install Matlab and I type
```
sudo sh /home/armen/Downloads/Matlab.R2010b.UNIX/matu20Xb/install

```

I get this error, which stops installation right away:
```
eval: 1: /tmp/mathworks_29716/java/jre/glnxa64/jre/bin/java: Permission denied
```

Maybe it something to do with OpenJDK Java? Do I need to install non-free JDK from Oracle?

---

### Post by thomas_toscani on 2012-03-12
I had the same error message.

Try mounting the ISO instead of extracting it.

Run the installer script from the mounted ISO directory or from CD itself.

Ooops.  Also fixed here:

[http://ubuntuforums.org/showpost.php?p=10654216&postcount=16](http://ubuntuforums.org/showpost.php?p=10654216&postcount=16)

---

### Post by overdrank on 2012-03-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

