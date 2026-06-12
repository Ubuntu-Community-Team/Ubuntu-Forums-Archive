---
title: "no root access"
date: 2011-12-24
forum: Desktop Environments
---

### Post by DeceptiveHornet on 2011-12-24
Hello,

Yesterday i switched my regular profile to not being able to administrate the system to avoid messing something up, as i have it just the way that i want it. I made sure to remove the admin privvys for my regular account while enabling the root one so i can log in on that one when i actually need to do somethinng. 

But somehow, the computer keeps telling me it is forbidden / not enabled to log in with root. Am i permanently locked out from root access? I can't even sudo with this account. I'm running Kubuntu 11.04

---

### Post by lisati on 2011-12-24
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And please don't swear in your posts, this forum aims to be family friendly.

---

### Post by haqking on 2011-12-24
> **DeceptiveHornet said:**
> Hello,

Yesterday i switched my regular profile to not being able to administrate the system to avoid messing something up, as i have it just the way that i want it. I made sure to remove the admin privvys for my regular account while enabling the root one so i can log in on that one when i actually need to do somethinng. 

But somehow, the computer keeps telling me it is forbidden / not enabled to log in with root. Am i permanently locked out from root access? I can't even sudo with this account. I'm running Kubuntu 11.04

the whole point of [sudo]("https://help.ubuntu.com/community/RootSudo") is to carry out root actions without logging in as root as it is bad practice and not needed, as for messing things up you shouldnt be able to as you need to use sudo, if you are in the habit of messing things up then logging in as root is even a worse idea ;-)

read the link above and then restore sudo for your account.

see here [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

and here for root password issues if you have them [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

