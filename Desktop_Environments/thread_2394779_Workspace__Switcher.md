---
title: "Workspace  Switcher"
date: 2018-06-21
forum: Desktop Environments
---

### Post by bowery on 2018-06-21
I have installed Ubuntu 18.04 and have put Unity over the top the Workspace Switcher looks like this when I am looking at all of them.

[https://www.google.com/imgres?imgurl=https%3A%2F%2Fi.stack.imgur.com%2Fnrc0r.png&imgrefurl=https%3A%2F%2Faskubuntu.com%2Fquestions%2F77806%2Fhow-can-i-change-the-number-of-workspaces-in-workspace-switcher&docid=emyBTE7UaAfc8M&tbnid=oXUdALiw6uHvJM%3A&vet=10ahUKEwjhmavPk-TbAhUG6bwKHVeoCD8QMwg8KAMwAw..i&w=1366&h=768&bih=903&biw=1280&q=workspace%20switcher&ved=0ahUKEwjhmavPk-TbAhUG6bwKHVeoCD8QMwg8KAMwAw&iact=mrc&uact=8](https://www.google.com/imgres?imgurl=https%3A%2F%2Fi.stack.imgur.com%2Fnrc0r.png&imgrefurl=https%3A%2F%2Faskubuntu.com%2Fquestions%2F77806%2Fhow-can-i-change-the-number-of-workspaces-in-workspace-switcher&docid=emyBTE7UaAfc8M&tbnid=oXUdALiw6uHvJM%3A&vet=10ahUKEwjhmavPk-TbAhUG6bwKHVeoCD8QMwg8KAMwAw..i&w=1366&h=768&bih=903&biw=1280&q=workspace%20switcher&ved=0ahUKEwjhmavPk-TbAhUG6bwKHVeoCD8QMwg8KAMwAw&iact=mrc&uact=8)

I want it to look like this.

[https://www.google.com/imgres?imgurl=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2F6%2F64%2FUbuntu_Unity_Workspace_switcher_-_Uk.png&imgrefurl=https%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FFile%3AUbuntu_Unity_Workspace_switcher_-_Uk.png&docid=UZmqj6gvQQETOM&tbnid=OeYS-a3lLrmpQM%3A&vet=10ahUKEwivuuqCq-TbAhXMUrwKHdUPDLkQMwhDKAowCg..i&w=1680&h=1050&bih=903&biw=1280&q=Workspace%20switcher&ved=0ahUKEwivuuqCq-TbAhXMUrwKHdUPDLkQMwhDKAowCg&iact=mrc&uact=8](https://www.google.com/imgres?imgurl=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2F6%2F64%2FUbuntu_Unity_Workspace_switcher_-_Uk.png&imgrefurl=https%3A%2F%2Fcommons.wikimedia.org%2Fwiki%2FFile%3AUbuntu_Unity_Workspace_switcher_-_Uk.png&docid=UZmqj6gvQQETOM&tbnid=OeYS-a3lLrmpQM%3A&vet=10ahUKEwivuuqCq-TbAhXMUrwKHdUPDLkQMwhDKAowCg..i&w=1680&h=1050&bih=903&biw=1280&q=Workspace%20switcher&ved=0ahUKEwivuuqCq-TbAhXMUrwKHdUPDLkQMwhDKAowCg&iact=mrc&uact=8)

---

### Post by deadflowr on 2018-06-21
Not sure what you want is possible with two monitors.
Closest you might get is using the expo setting for one big wall instead of one wall per output.
But that's still goofy looking.
expo can be set in ccsm (compizconfig-settings-manager; which you'd need to install)

---

### Post by bowery on 2018-06-21
I had it working before in Ubuntu 14.04 I just want 8 workspaces to fill the entire screens without empty space around them so I can read everything at a glance. That is four workspaces on each screen with no space around them.

---

### Post by deadflowr on 2018-06-21
Sorry, it looked like what dual monitor output looks like.
I think it's the aspect ratio setting in  ccsm > expo > appearance.
About the best you can get with unequal workspaces (4x2)
If you where to use an even workspace like 3X3, that will full the screen without the need to toggle the aspect ratio setting.

At least that's what I see.

---

### Post by mc4man on 2018-06-21
> **bowery said:**
> I had it working before in Ubuntu 14.04 I just want 8 workspaces to fill the entire screens without empty space around them so I can read everything at a glance. That is four workspaces on each screen with no space around them.
Try the expo option of "One big wall" in Multi Output Mode

---

### Post by bowery on 2018-06-22
Yes thanks the one big wall in expo worked. It is perfect except the side bar wont disappear and pushes everthing about 2cm to the right. see image below (the sidebar disappears when I am in full screen)

[https://drive.google.com/file/d/1SxPl3ZxOVc4rxaxLjJPXWii0fwRqi0uI/view?usp=sharing](https://drive.google.com/file/d/1SxPl3ZxOVc4rxaxLjJPXWii0fwRqi0uI/view?usp=sharing)

---

