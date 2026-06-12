---
title: "After most recent updates, mount/unmount usb requires password"
date: 2015-10-26
forum: Desktop Environments
---

### Post by IanBal on 2015-10-26
I updated my Ubuntu 14.04 laptop last night.  Since the update, when I plug in a usb stick I need to provide a password.  Also if I want to unmount it I have to provide a password.  This is very annoying.
This was not the case until last night.  
I have tried searching for a solution but with no success.  I have seen some message in the requester about polkit however I haven't made progress in finding understandable or usable information for that either.

Also after the update last night I am no longer able to turn the wifi off using the control panel.  I suspect the two issues are connected.

What can I do to restore the previous behaviour?  That is, plug the usb device in and mount it without having to put in a password. 
Also how can I restore the previous ability to turn the wifi off and on as I was able to before?
Are there any other surprises in store for me with regard to the updates?

---

### Post by Dennis N on 2015-10-26
I have seen the same behavior several times after certain updates, but it is fixed by merely log out and log in. Have you logged out (or restarted) since these updates? I ask because some users infrequently turn off their systems.

---

### Post by grahammechanical on 2015-10-26
Policy Kit (polkit) or pkexec is a method of forcing an authentication request when the user takes certain actions. You will find the policies in /usr/share/polkit-1/actions. These policies also control who has the authority to authenticate the action. If you are interested and purely from the point of view of education, the policy that you are looking for is called org.freedesktop.udisks2.policy. The defaults are

> <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>

Regards.

---

### Post by IanBal on 2015-10-27
I am one of those who stays logged in for ages ;-)
In the end rebooting solved the immediate problem.  It seems however there are other problems that I have to investigate, session save and restore for example.
I will check out the polkit configurations when I have more time, it seems everyone will have to do that in the future.
Thanks for your help!

---

