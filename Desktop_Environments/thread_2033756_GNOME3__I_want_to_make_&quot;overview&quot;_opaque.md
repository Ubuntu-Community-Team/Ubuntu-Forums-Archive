---
title: "GNOME3 : I want to make &quot;overview&quot; opaque"
date: 2012-07-26
forum: Desktop Environments
---

### Post by vexorian on 2012-07-26
Edit: Yeah, I actually meant "completely transparent" rather than opaque. I already know how to make it opaque, just edit the CSS bellow...

This is what I'd like to happen:

[ATTACH]221845[/ATTACH]

It is probably not noticeable, but there is no dark shadow all over my wallpaper. So when I go to the overview, I can actually look at my wallpaper, rather than a more depressing, darkened version of it.

I just can't find the option to replace the partial opacity of the overview into complete transparency. Ok, I did find the CSS entry for the overview:

```

#overview {
/*    stuff*/
}

```

But if I replace its background with a completely transparent one, it does not work. So, there are TWO objects getting painted in the overview.

You are about to ask, if I have a screenshot of it, then I can already do it. Well,... kinda, here is what I did:

```

#overview {
    spacing: 12px;
    background: url('/home/vx/wallpaper') ;
}

```

It is just a workaround. But I would have to replace the url() everytime I change my wallpaper. There is got to be an easier way, right?

---

