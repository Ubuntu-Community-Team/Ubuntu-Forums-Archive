---
title: "apt-get update error"
date: 2009-05-18
forum: General Help
---

### Post by crazymoonboy on 2009-05-18
Hi,

I am trying to install one software from a https server and I already have my user name and password. BUT, Here

My user name is email id i.e., [email]abc@def.com[/email]
My password: password

and I am trying to get files from [www.example.net/somefile](www.example.net/somefile).

Now, I added the whole line in /etc/apt/sources.list file as below:

deb [https://abc@def.comassword@example.net/somefile](https://abc@def.comassword@example.net/somefile)
deb-src [https://abc@def.comassword@example.net/somefile](https://abc@def.comassword@example.net/somefile)

Now, I executed apt-get update command and it is giving the below error:
Couldn't resolve host 'def.comassword@example.net'

It is not taking my entire email id as my user name.

How can I give correctly in /etc/apt/sources.list file? Please help me.

Thanks in advance.

Regards,
Chandra.

---

### Post by darsie on 2009-05-18
Hi Chandra,

Is that a repository you are attempting to download from? Could you provide the real URl perhaps?

---

### Post by crazymoonboy on 2009-05-18
Hi,

Thank you for your response. I already tested using wget command by downloading one single file. But, I am getting this error, when i added in sources.list file only. 

I just read that if user name contains @ sign, we need to do something. That is I dont know. If we are giving email id directly as user name, it is taking only after the @ part in my user name. So, I explained with example.

Please help me. Thank you.

Regards,
Chandra

---

