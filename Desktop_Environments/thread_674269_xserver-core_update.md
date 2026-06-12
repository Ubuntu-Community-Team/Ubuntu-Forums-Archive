---
title: "xserver-core update"
date: 2008-01-21
forum: Desktop Environments
---

### Post by jimbo99 on 2008-01-21
Though this may have been covered in an earlier thread (I did look and found nothing on topic), I seem to be a bit upset at how the Ubuntu folks are distributing their updates, particularly an update tied so entirely to the theme of the idea behind Ubuntu.

Ubuntu is a product made for the human being in us.  As of about 3 days ago Ubuntu failed to allow me to log in to the desktop.  It would present the graphical log in prompt but when the user name and password were entered it would act like it was going to take me to the desktop, but would stop and take me back to the log in prompt.

The issue is with the video drivers and Xserver.  I was prompted about 3 days ago to update the xserver-core and some other components.  I took those updates and restarted my computer.  When I came back in the issue presented itself.

I then went and reinstalled the nVidia drivers and was able to get into the desktop and use it.

Now that's one thing. For me, well, OK.  I can deal with the problem except when I'm trying to address my customer's problems and have to use the computer to look things up.  When I can't do that I look bad to them and they are unhappy that I am taking their time up.

So, I had a customer come into the store and he stated he was having the same issue.  Exactly the same issue.  He was a bit upset.  I tried to explain the situation and told him to bring in the computer and I'd update his video drivers.

He did, the drivers installed and the GUI worked again.

What do you guys not understand about "being a human being"?  Do you not understand that you don't update this stuff that in such a way could make the OS unusable by the very people you are trying to make this product for?  We, as a people need to make it easier to get others to use the product, but if one simple update causes such great issue where the user can't use their own computer because you update something, then something is very very wrong.  Your house is not in order.

I'd say to Mark Shuttleworth:  Don't let them do this again.  Do not issue the update wthout a total fix/update that works.

So, I fixed this guys video issue.  Only this morning he comes into my store and states it is happening again.

What do you know?  Ubuntu updated these core files again and caused the SAME exact issue.  I had to resolve it for myself a second time and now I have to resolve it for him.  I do not want to put my customers through this.  EVER.  Who cares what you think of them or their responsibility to the Open Source idea, or even mine.  Do NOT do this again to your users.

I can only imagine how many users have this same issue and how many of those have no idea how to resolve the issue themselves.  It is just horrible that the Ubuntu people would allow this to happen once, a single time.  But to allow it to happen 2 times in a 3 day period is just terrible.

I don't care about security fixes if it causes the computer to become unusable.  Period.  I'd rather deal with the security issues the way they were before the fix (I had a working computer).

DO NOT DISABLE OUR COMPUTERS DUE TO ISSUES WHICH REQUIRE SECURITY FIXES!

---

### Post by cmulcahy on 2008-01-21
Jimbo99:

Thanks for posting.  I found this while working through my own issues.  My desktop stopped working.  It seems that for the last several days many people have been experiencing the same issues with no resolution so far.  I am glad you solved your problems and may have pointed me towards my own solution.

I BELIEVE I am using nvidia-glx-new.  Were you using dpkg-reconfigure nvidia-glx-new to fix the problem or were you removing and reinstalling the package?

Thanks

---

### Post by buntu_hugenewbie11 on 2008-02-01
Does this problem still exist??
And how do I check which nvidia drivers I have and which ones should I install after the update?
And how?
Sorry I am terrible at doing this.

---

