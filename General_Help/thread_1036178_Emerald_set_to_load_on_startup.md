---
title: "Emerald set to load on startup?"
date: 2009-01-10
forum: General Help
---

### Post by smirnoff76 on 2009-01-10
Hi all, 

I have downloaded some emerald themes froms from gnome-look.org and applied them and they work a treat. 
Just wondering if anyone can tell me how to set emerald to load on startup?

Thanks!

---

### Post by Ivo Moelans on 2009-01-10
Open *System&#8594;Preferences&#8594;Sessions*. Click *Add*. In the field *Command* type *emerald --replace* (mind the space between *emerald* and *--replace*). For *Name* type *Emerald*. *Description* is optional.
Save. See that the box is checked.

That's it. Emerald will be loaded when you log in.

---

### Post by smirnoff76 on 2009-01-11
Hi Ivo Moelans thanks for the reply, tried that but isn't working? When I load through the compiz fusion icon works fine but not using the emerald --replace command? 
Any idea's?

Thanks

---

### Post by howefield on 2009-01-11
How about adding to the compiz settings, load up compiz settings manager and go to Window Decoration and type in the Command field

```
/usr/bin/emerald
```

---

### Post by Ivo Moelans on 2009-01-11
Forgot about that.

But I think it might be

```
/usr/bin/compiz-decorator
```

in the *Command* field.

Anyway, you probably need the item checked in *Sessions* also.

---

### Post by smirnoff76 on 2009-01-11
just tried adding /usr/bin/compiz-decorator to session too but that isnt working either?

---

### Post by howefield on 2009-01-11
Did you try /usr/bin/emerald ?

And no, you don't need it checked in sessions also.

---

### Post by Ivo Moelans on 2009-01-11
*/usr/bin/compiz-decorator* should go in *System&#8594;Preferences&#8594;CompizConfig Settings Manager*, category *Effects*, item *Window Decoration*, field *Command*.

*emerald --replace* in *Sessions* (as explained in post #2)

Edit
@ howefield

That's how it works (and it *does* work) on my system and that's also how I learned it from some how to some time ago. But I am going to try your method also.

---

### Post by Ivo Moelans on 2009-01-11
Tried it out and it works!

@ smirnoff76: howefield's method is cleaner, so better use that.

@ howefield: thank you, I learned something new.

---

### Post by howefield on 2009-01-11
> **Ivo Moelans said:**
> That's how it works (and it *does* work) on my system and that's also how I learned it from some how to some time ago. But I am going to try your method also.

Show me where anyone said it didn't work ?

I am sure I am not the only one who has emerald working without putting it in the sessions menu and using /usr/bin/emerald in compiz settings > window decorator.

That's the beauty of these operating systems, there is always more than one way to accomplish something.

---

### Post by howefield on 2009-01-11
> **Ivo Moelans said:**
> Tried it out and it works!

@ smirnoff76: howefield's method is cleaner, so better use that.

@ howefield: thank you, I learned something new.

Thank you Ivo, glad to have helped.

---

### Post by Ivo Moelans on 2009-01-11
Yes it is, isn't it? And it is always a pleasure to learn one of those new ways. Nevertheless I have the impression that your method is somehow cleaner.

---

