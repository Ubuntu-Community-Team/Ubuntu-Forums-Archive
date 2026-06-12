---
title: "Video missing something"
date: 2009-03-31
forum: General Help
---

### Post by Otto-C on 2009-03-31
Using 8.04.2.
When reading a news story and there is the opportunity to view a
video and clicking on it the video does not play. But going to the
Youtube site and accessing the video it plays. My question is what 
am I missing or am I?
tia
otto-c

---

### Post by Therion on 2009-03-31
If I had to guess, you're missing Java.  YouTube is primarily Flash based.

Fire up a terminal and cut and paste the following code into it.  

Enter your password when it's asked for and then just follow the prompts.

We're going to install Ubuntu Restricted Extras as well, just to help cover all your bases in one fell swoop:

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin ubuntu-restricted-extras
```

---

### Post by Otto-C on 2009-04-04
You hit the nail on the head. The above solution
solved the problem.
Thanks
otto-c

---

