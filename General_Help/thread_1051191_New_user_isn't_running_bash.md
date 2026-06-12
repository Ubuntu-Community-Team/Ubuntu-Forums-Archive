---
title: "New user isn't running bash"
date: 2009-01-26
forum: General Help
---

### Post by sdlyr8 on 2009-01-26
I just created a new user on my box so my friend could ssh in and work on a website we're making, and when he gets on, instead of the usual prompt of "stephen@stephen-desktop:~$", all he gets is "$". I have to manually type "bash" to get everything the way it should be. what setting did I forget to set when I created his account and how to I made it use bash everytime he logs in?

Thanks

---

### Post by fragos on 2009-01-26
System-> Adminstration-> Users & Groups-> Unlock button-> Select user-> Properties button-> Advanced tab-> Enter /bin/bash inti Shell:

---

### Post by sdlyr8 on 2009-01-26
Thanks! I knew it would be something quick and easy

---

