---
title: "Privacy Settings for 12.04 lts"
date: 2015-02-05
forum: Desktop Environments
---

### Post by michael-piziak on 2015-02-05
I know there was much ado about privacy settings in Unity and that 14.04 lts made it easy to address.

But in 12.04 lts, what is the best way to tweek the privacy settings so that no information is sent to the internet on what you search for in Dash Home.

In the attached screenshot, I think this is where one would do it.  But I don't want "record activity" off as I do want to record my local activity (like what apps I used recently).  I just don't want any search in Dash Home to go out to the internet.

---

### Post by deadflowr on 2015-02-05
12.04 doesn't have online search.

Well, mostly, it doesn't have online search.
12.04 only has online video search, but it only searches video sites, and you must be in the video scope.

You can then also make it not search online videos by going to the video scope and then expand the filter tab and selecting the "My Videos" tab only.
I believe you can also remove the feature, I think the package for it is unity-scope-video-remote.

But again, that is the full-scope(lol) of 12.04's search features from the dash.
Which is why there is no off button. Like in newer releases like 14.04's turn off online search.

Added:
( Also, there is another scope called unity-scope-musicstores, but I really don't remember if it is pre-installed or not.
My only 12.04 doesn't have it, but that doesn't mean I did not remove it long ago...)

---

### Post by michael-piziak on 2015-02-06
Thanks so much.

I changed the filter for videos to just "my videos."  Great.

Now, it does have a music scope also, but as you can see in the screenshot below it can't be turned off so easily when clicking filters.  As I typed in Michael Jackson and it sent my search out to the web and returned a result.

?

---

### Post by deadflowr on 2015-02-06
yeah, looking it over it should be a default package "unity-scope-musicstores"

The reason I'm not seeing it is that it depends on the rhythmbox-ubuntuone package.
I removed all ubuntuone packages, which also removed the musicstores package.

So basically 12.04 only allows search online for videos and music.
If you want to limit the search you can either try to filter the search, or remove the scope packages.
They would be
unity-scope-video-remote >> for the video search
and
unity-scope-musicstores  >> for the music search.

An aside: If you have the ubuntuone packages you should remove them, as they are totally pointless now.
I followed this
```
dpkg -l | grep ubuntuone
```
from here
[http://askubuntu.com/questions/484328/how-do-i-stop-ubuntu-one-from-telling-me-its-file-service-will-be-shutting-down](http://askubuntu.com/questions/484328/how-do-i-stop-ubuntu-one-from-telling-me-its-file-service-will-be-shutting-down)

worked as expected, nothing weird or anything happened upon the package removal.

Either way, those are some options.
Best of luck.

---

### Post by michael-piziak on 2015-02-06
Thanks.  I removed Ubuntu One already.

Thanks again.  Marking this thread as solved.

---

