---
title: "2 computers just alike"
date: 2009-01-04
forum: General Help
---

### Post by Silvernail on 2009-01-04
I have a laptop and a desktop with 8.04 installed on each.

The laptop has been in operation longer and I have installed some applications on it that I would like to have on the DT.

Is there an application that will scan my laptop and make a list so I can check it against what I have on my desktop and install the difference?

Or do I need to start thing about writing a script to do that?

TIA
Dave

---

### Post by albinootje on 2009-01-04
> **Silvernail said:**
> 
Is there an application that will scan my laptop and make a list so I can check it against what I have on my desktop and install the difference?


You can try the following :
```

dpkg -l > comp1.txt              (done on comp1)
dpkg -l > comp2.txt              (done on comp2)
diff comp1.txt comp2.txt

```

---

### Post by Silvernail on 2009-01-04
OK, now  I think I have information overload.
I see I have some manuals to read.

Thanks,  I'll be  back.
Dave

---

### Post by albinootje on 2009-01-04
> **Silvernail said:**
> OK, now  I think I have information overload.


Actually, you can probably also compare the differences between the content of /var/cache/apt/archives/ on both machines.
And then you could copy the content of that directory from the laptop with the older installation over to the new one, that'll save you downloading files :)

---

