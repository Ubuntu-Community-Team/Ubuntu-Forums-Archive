---
title: "Medibuntu servers down causes MAJOR headaches!"
date: 2008-12-29
forum: General Help
---

### Post by JohnFH on 2008-12-29
I came across a problem today which caused my server to hang and my desktop web access to be unbearably slow.  I have spent most of today trying to figure out what the **** was going wrong and am really annoyed that it's due to medibuntu servers being down.

All software updates were hanging because of medibuntu and that meant internet access was severely disrupted.  I'm just ever so slightly annoyed and so have the following questions and am open to any further comments you may have.

Actually it boils down to one overall question really:
Why should the apt-get update system RELY on repository servers being up?  If one of the servers mentioned in /etc/apt/sources.list is down, the whole update process will never complete and that causes my server to hang and my desktop web access to fail completely!  Why should a dead server affect my systems so much???!!!

---

### Post by Skripka on 2008-12-29
If I had to guess I'd say it could be due to the massive internet problems the US midwest has had over the last 24-36 hours.

---

### Post by dcstar on 2008-12-29
> **JohnFH said:**
> ........
Actually it boils down to one overall question really:
Why should the apt-get update system RELY on repository servers being up?  If one of the servers mentioned in /etc/apt/sources.list is down, the whole update process will never complete and that causes my server to hang and my desktop web access to fail completely!  Why should a dead server affect my systems so much???!!!

The update process WILL complete - after the system waits for timeouts from the non-responding repositories.

If you let it run in background (like it is supposed to) you won't even notice the "problem".

---

### Post by scootre on 2008-12-29
> **JohnFH said:**
> 
Why should the apt-get update system RELY on repository servers being up?  If one of the servers mentioned in /etc/apt/sources.list is down, the whole update process will never complete and that causes my server to hang and my desktop web access to fail completely!  Why should a dead server affect my systems so much???!!!

Perhaps someone could explain that to me as well.

I am getting failures on Medibuntu updates - headers failing to download.

The error I get only happens on fetching number 35 out of 36. It times out trying to get

```

http://<repository> intrepid-security/multiverse sources

```

Where <repository> is any that I try: Ubutnu default, Internode (here in Australia), aarnet (Australia) etc.

The error is:

```

   http://packages.medibuntu.org/dists/...tion-en_AU.bz2 Connection failed [IP: 88.191.79.39 80]

      Some index files failed to download, they have been ignored, or old ones have been used instead.

```

And the IP address it returns is not pinging or resolving.  So something's amiss.  

But why are they failing if I am using Australian (or any other) repositories?  The 88.x.x.x IP is not here in Australia.

---

