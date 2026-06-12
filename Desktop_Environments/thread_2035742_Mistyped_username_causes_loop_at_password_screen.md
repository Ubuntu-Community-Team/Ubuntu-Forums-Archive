---
title: "Mistyped username causes loop at password screen"
date: 2012-07-31
forum: Desktop Environments
---

### Post by peabrane on 2012-07-31
This is a minor irritation, but I think it may be a bug. Does anyone else have the same problem or a solution?

I have Lubuntu installed on an Asus Netbook and on a venerable HP Omnibook laptop. Both show the same problem. However, my Ubuntu desktop does not show this problem.

For extra security, I have set "greeter-hide-users=true" in lightdm.conf. I like my usernames to be hidden. If I enter my username correctly, no problems. However if I mistype my username, I get to the password entry and cannot get back to the username screen. Eventually, the password entry box goes grey. Hitting log-in or cancel has no effect at any stage on the password screen. All I can do is to shutdown and start again.

If greeter-hide-users to false, the situation would not arise as there is no username entry.

Any views from the very helpful and knowledgeable people out there would be gratefully received.

---

### Post by Toz on 2012-08-06
Looks like a bug. See [here]("https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/974610") and [here]("https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/990315").

---

### Post by peabrane on 2012-08-07
Thanks Toz,

I did try to check the bug list before I posted but for some reason, it did not occur to me to use lightdm as a key. Oops.

Thread closed as requested.

Thanks again.

---

