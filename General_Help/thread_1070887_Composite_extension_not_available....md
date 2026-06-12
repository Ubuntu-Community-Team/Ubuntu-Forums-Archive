---
title: "Composite extension not available..."
date: 2009-02-15
forum: General Help
---

### Post by JimBuntu on 2009-02-15
What is going on? I had Ubuntu 7.1 on my laptop with everything working properly. All of the Compiz graphics where working perfectly. Then I upgraded to 8.04 then 8.10 and now its saying "Composite extension not available" every time I try to click on the "extra" setting in the visual effects window. No extra graphics, no fun.

I also have some new error on start up saying something like " Error: aperture beyond 4gb. Ignoring" . I don't know if that has anything to do with the Compiz problem but its definitely new.

---

### Post by JimBuntu on 2009-02-16
bump

---

### Post by JimBuntu on 2009-02-17
anyone?

---

### Post by geirha on 2009-02-18
«Composite extension not available» typically means that you don't have a display driver that can do 3d installed. What's the output of ```
sudo lshw -class display
```

What do you see in System -> Administration -> Hardware drivers?

---

