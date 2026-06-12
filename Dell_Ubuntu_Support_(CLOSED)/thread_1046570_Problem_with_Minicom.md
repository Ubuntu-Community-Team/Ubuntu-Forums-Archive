---
title: "Problem with Minicom"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tan Man on 2009-01-21
When I try to connect to a cisco router using Minicom, I cannot get the line for commands up. Is this a problem with the TTY8? If so, then how do I fix it?

---

### Post by Cannotcompute on 2009-01-21
You should probably post this in one of the more generic forum sections, since this isn't a Dell hardware issue.

---

### Post by Tan Man on 2009-01-21
> **Cannotcompute said:**
> You should probably post this in one of the more generic forum sections, since this isn't a Dell hardware issue.

Well it is a problem with my school's Dell computer. My networking teacher told me to post this here.

---

### Post by Vesperatus on 2009-03-23
I have the same issue with Minicom.

The weird part is I know it is correctly configured because if I type stuff and press enter, the close minicom and open the same connection with gtkterm I can see the stuff I typed with minicom... 

Anyway, I tried to find some solutions regarding minicom and could'nt find any. After a while, I juste installed cutecom ( sudo apt-get install cutecom ). 

It is really simple to configure and it looks better than Gtkterm ( I never figured out why gtkterm adds TWO \n after each input line ..... )

I suggest you use cutecom. It work in under 1 minute for me.

---

