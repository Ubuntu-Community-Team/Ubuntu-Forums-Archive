---
title: "Weird Terminal Issues"
date: 2009-03-29
forum: General Help
---

### Post by ghempton on 2009-03-29
I am running a vanilla installation of 8.10 Desktop on my relatively new thinkpad T61 and I occasionally see weird characters outputted in the terminal, to the extent that sometime the terminal becomes unusable afterwards. For instance, if I do a mysqldump directly to the std out (instead of dumping to a file), the following happens:

```
mysqldump -u root -p schema
```

[IMG]http://hempton.com/misc/weird2.png[/IMG]

As you can see, my command prompt is now comprised of random ascii characters, and when I type into the prompt, weird characters appear as well. What the screenshot doesn't capture, is the title bar of the window is also comprised of these characters.

Also, when I run other programs I see things like the following:

[IMG]http://hempton.com/misc/weird.png[/IMG]

Where the weird characters are normally the vnc reflector version when I run this under cygwin on windows.

Anyone know what is going on?

Thanks in advance,
Gordon

---

