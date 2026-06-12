---
title: "Any way to 'see' running package managers?"
date: 2009-05-06
forum: General Help
---

### Post by OxentroT on 2009-05-06
Yes I sometimes have package managers running however they sre not visible.
Is there any way to view or make these running managers visible as they do their thing?:confused:

---

### Post by danwood76 on 2009-05-06
How do you run package managers invisible?

If you use command line package managers froma  script you can just run the script from a terminal and it will output all the relevant info.

---

### Post by OxentroT on 2009-05-06
Thankyou for your response.

I at times have the notification for updates, I right click on it to install the updates where I am then told that there is already a package manager running. Even when I try to open it through the administrative menu.
It states that their is already a manager running. Even after the fact that any *known* processes carried out by 'apt-get' or 'pkg manager' prior to that have since finished or been interrupted by some sort of error.

And I have tried, on a couple of occasions, the -f commands that were suggested by the errors which would then return another error.

---

### Post by danwood76 on 2009-05-06
It will give you that response if synaptic or aptitude (apt) is running.
If either of those have crashed it will be the case that they havent unlocked the process. (which shouldn't happen)

When this happens check the list of running processes in system monitor (make sure show all processes is checked) and see if apt or synaptic are running.

As I said this shouldnt happen, but it will also happen is another user on your system has any of the above programs open also.

---

### Post by OxentroT on 2009-05-06
Everything seems to be back to a smooth running after I entered one of the maintenance commands. I thankyou for your assistance, hopefully all of this stays as is. :guitar:

---

