---
title: "Issues with KDM"
date: 2009-10-05
forum: Desktop Environments
---

### Post by Neremor on 2009-10-05
Hello!

I've a new PC with a new monitor. The format of my monitor is 16:9. The setup of my graphic card worked perfectly and i can use the resolution of 1920x1080. But tis resolution is only working after i logged in, kdm is using some other resolution with stripes on the left and the right side. It seems like kdm isn't using the 16:9 but the 4:3 aspect ratio. Any Ideas how to correct this?

And I've another question, just for interesst; is is possible to change the background-image of the standard kdm theme? Or even better, make it to be the current desktop background?

Thanks in advance for every help and please excuse my bad english,
Jonathan

---

### Post by Neremor on 2009-10-07
does no one have any idea? :(

---

### Post by kellemes on 2009-10-07
> **Neremor said:**
> Hello!

I've a new PC with a new monitor. The format of my monitor is 16:9. The setup of my graphic card worked perfectly and i can use the resolution of 1920x1080. But tis resolution is only working after i logged in, kdm is using some other resolution with stripes on the left and the right side. It seems like kdm isn't using the 16:9 but the 4:3 aspect ratio. Any Ideas how to correct this?

And I've another question, just for interesst; is is possible to change the background-image of the standard kdm theme? Or even better, make it to be the current desktop background?

Thanks in advance for every help and please excuse my bad english,
Jonathan


This is what I'd try..

Open up /etc/X11/xorg.conf and look for a line like this..
```
virtual xxxx xxxx
```
You can either change the values with your preferred resolution..
```
virtual 1920 1080
```
or comment out the line completely...
```
#virtual xxxx xxxx
```

---

