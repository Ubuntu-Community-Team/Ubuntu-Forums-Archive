---
title: "Server backup help"
date: 2006-07-12
forum: Desktop Environments
---

### Post by kandalar on 2006-07-12
Hello,
This is my first time posting here as I have just recently switched to Ubuntu.
I have found your forums to be amazingly helpful and the community here is by far the least uppity. 
I have a question that may be more of a general linux question than an Ubuntu question, but here it goes:

I have this customer for whom I programmed a large intricate website and he is a very paranoid man. He already has backups at rackspace and I backup his database nightly into a tar file on his server.
Recently, he has gotten the idea that Rackspace may explode one day and that he needs to get another server and stick it in his house so he can just point the DNS at his server when Rackspace gets destroyed in some terrorist bombing. So he went out and purchased a very expensive tower server from dell that sounds like a jet engine when you turn it on and has rehat enterprise already on it.

He wants me to make it so that his local server is running the exact same files as the remote server, and hopefully even the same versions of the software. 

I don't really know the repurcussions of this, seeing as I have never tried anything like this. He says he bought almost the identical server to the one they have at rackspace, but I don't know how true that is.  I assume there would be big incompatibility problems if the hardware is at all different and we are just running the system off of a mirror of that system. Is there some tool out there for Ubuntu or Redhat that makes this type of thing easy? I know I could just make it so I backup the configuration files for apache and the whole database every night. But what if the version of something changes? I guess you can see where I am going with this. 

BTW: I am using EMBPerl/PostgreSQL for the database and code, I guess I would have to watch for newer versions of that too.

BTW2: I don't consider myself a server admin, I am just trying to help this guy out with his paranoia. ;) 

I am also not totally against just removing redhat and putting Ubuntu on there either. 

Thanks for the help. Hope I was clear enough. :D

---

### Post by Dubbayoo on 2006-07-12
sounds like a job for rsync to me.

---

### Post by lamego on 2006-07-12
There is nothing paranoid with your customer, he is just conscious. What you are trying to achieve is a small piece of a DRP (Disaster Recovery Plan) with an online backup server.
I agree with Dubbayoo that rsync is a good tool to do such copies, the great advantage from rsync compared to the other standard copy utilities is that it is able to do incremental backups (just copy the files which are different), backups will run much faster and will use less bandwidth.
Your main concern should also be with the data integrity, I don't have experience with PostgreSQL but in general you can't just copy the data files while the database is online, probably you would need to shutdown the database or use some database specific tool to create the data backups.

---

### Post by kandalar on 2006-07-12
I will give that a try, thanks for the advice. I will have to do some reading on Rsync. Thank you very much.

---

### Post by lindyslack on 2006-07-12
I third the rsync motion... I use it to back up my laptop under cygwin in windows and ... well Ubuntu... to a remote machine... Works wonderfully...

---

### Post by kandalar on 2006-07-13
I have been researching it a little and I see that I will have to backup the database and possible the email files differently since they may be open for writing.
I already know how to do that with the database since I am already making backups of that. 

However, I am not sure what the problems may be with backing up email. 
They only have two email addresses, so I guess they aren't checking their email too often, but they are using their server as the mail server. 

Is there a guide out there somewhere on how to backup the mail? I assume they are using the defualt mail server in redhat. Thanks again.

---

