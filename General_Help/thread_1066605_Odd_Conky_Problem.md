---
title: "Odd Conky Problem"
date: 2009-02-11
forum: General Help
---

### Post by dse.37 on 2009-02-11
I've used Gutsy since it's release and just wiped my drive clean for Intrepid (which I must say I'm not overly impressed with).

Anyway, up until now I've had no problem with the following in my conky configuration:

```
${if_running /usr/lib/exaile/exaile.py}${color ffffff}${execi 5 exaile --get-title} ${execi 5 exaile --get-length}$color
${color 888888}${execi 5 exaile --get-artist}$color
${color 555555}${execi 5 exaile --get-album}$color
${else}${color 888888}no media playing$color${endif}
```

As you see, it would display the following:

Song Title 0:00
Artist
Album

unless Exaile wasn't running and then it would output "no media playing."

But there's something going on now that conky isn't liking and is throwing a few different things depending on what I do.

If I leave the above as it is conky will only display "no media playing," but if I remove the $if_variable along with the $else then conky outputs the song information as it should but with "location: /usr/lib/xulrunner-1.9.0.6/libxpcom.so before 3" under each line.

I've added a screenshot of the problem. I hope somebody can help.

Thanks in advance.

---

### Post by Tibuda on 2009-02-11
try to run```
exaile --get-title
exaile --get-length
exaile --get-artist
exaile --get-album
``` in your terminal. these commands' output is what conky uses to fetch your player info.

---

### Post by dse.37 on 2009-02-11
It throws the same output as conky. I'm completely stumped.

---

### Post by Tibuda on 2009-02-11
So it has nothing to do with conky, but with exaile.

---

### Post by dse.37 on 2009-02-11
If that's the case then why did it work flawlessly for I don't know how long in Gutsy? Same version of Exaile and conky.

The only thing changed here is the version of the os.

And if all was well with conky then wouldn't it at least give me that strange output when it's inside of the $if_variable too?

The only time I get anything out of conky to do with exaile is when I remove the if and else statements.

---

### Post by Tibuda on 2009-02-11
-REMOVED-

> **dse.37 said:**
> The only time I get anything out of conky to do with exaile is when I remove the if and else statements.That's strange. No idea why it happens. Try to replace ${if_running /usr/lib/exaile/exaile.py} for ${if_running exaile} but I'm not sure.

---

### Post by dse.37 on 2009-02-12
I've tried that too. Even in Gutsy the only way I could get if_running to work was with the full path.

Thanks for looking in and your suggestions though. :)

It's not the end of the world. As much as I'd like to keep my conky as simple and straight forward as possible it's just not worth the headache when there's kaivalagi's exaile python script.

---

### Post by Gerafin on 2009-04-26
I figured this out through sheer dumb luck.

Try

```
${if_running python /usr/lib/exaile/exaile.py}
```

The system monitor clued me in on this one :D It totally recognized the process as "python /usr/lib/exaile/exaile.py" so I took a wild guess that maybe Conky saw things the same way.

EDIT: No, okay, I was being stupid... it's just displaying the info because python is running >_<

Now I feel stupid.

---

