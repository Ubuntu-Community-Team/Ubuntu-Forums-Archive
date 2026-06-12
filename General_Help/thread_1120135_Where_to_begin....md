---
title: "Where to begin..."
date: 2009-04-08
forum: General Help
---

### Post by roodavis on 2009-04-08
I am filling in for a vacationing colleague and very much a unix newbie. I have been searching for answers all day and still not getting there, so a few pointers in the right direction will be most appreciated.

We have Ubuntu Server 8.0.4 running on a couple of SUn servers presenting a GNome desktop to SunRay thin-clients. My basic question is how to get up to speed really fast on managing the user preferences, homepage, FireFox settings, etc. I also need to know how to install plugins and get them to the users.  I don't mind reading and researching, I just don't know where to begin.

My specific question right now is how to disable pop-up blocker for all users on Firefox without having to instruct them on how to change preferences.

Any assistance greatly appreciated.

---

### Post by 3Miro on 2009-04-08
All the settings for Firefox are in 
```

/home/user_someone/.mozilla/firefox/some_random_tring.default/

```
(.default could be .some user if different users in Firefox are enabled)

However, none of the tests files in there had pop or popup as a string. Then I tried opening the sqlite files with a sqlite editor, but it could not read them (probably bad editor). I know it is in one of those, but don't know where. Also, if you find it, you will have to make a script that goes through all the folders for all the users and does the changes (might want to read on bash scripting).

What you want is in some of those files somewhere, however, I don't know where. This is a rather technical thing, most people here probably wouldn't know, I hope someone helps you though.

---

