---
title: "&quot;xwd -root&quot; does not capture screen properly (everything is black, except unity)"
date: 2012-11-21
forum: Desktop Environments
---

### Post by franik4ever on 2012-11-21
Today, I ran into weird issue.
OS: Ubuntu 12.04 LTS, unity2d

So, I ran the following command:

```
    xwd -root -out test.screen.root.xwd
```

and then opened this file with gimp. Here's what I get:

[IMG]http://i.stack.imgur.com/UeyXl.png[/IMG]

Then I tried:

```
    xwd -root | xwdtopnm | pnmtopng > Screenshot.root.png
```

And I got the following result:
Console output:
```

    xwdtopnm: writing PPM file
    libpng warning: Invalid sBIT depth specified

```

And the image itself:
[IMG]http://i.stack.imgur.com/A9Z4N.png[/IMG]

What can cause this? How can I fix it?

Regards,
Franik

---

