---
title: "Beryl problems"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by Wake Rider on 2007-09-01
Sometimes when using beryl, a window only appears as a black screen and won't display while others will. What can I do to prevent Beryl doing this? Has anyone else had the same problem and what did they do to fix it?

---

### Post by st33med on 2007-09-01
Can you try to turn off Beryl by doing this in the terminal?:

```
metacity --replace
```

That's if you have Ubuntu, not Kubuntu. Does that yield any change at all?

---

### Post by FuturePilot on 2007-09-01
It's a bug in the Nvidia driver. Sadly it's been around too long.
However, there is a workaround for it. Right click on the Beryl Manager and go to Advanced Beryl Options>Rendering Path>Copy

---

### Post by Wake Rider on 2007-09-01
It hasn't crashed my system or anything, it just won't display any windows. I restarted my computer and Beryl and it fixed it but I have had this problem happen before and it seems to be becoming more frequent. I am able to use Beryl-Manager to switch back to the KDE window manager whenever this happens. I don't know why the problem with the black screens started occurring, I have been using beryl for the last few weeks without any problems.

---

