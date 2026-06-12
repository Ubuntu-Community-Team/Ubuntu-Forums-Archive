---
title: "New user gets different window manager?"
date: 2009-03-16
forum: General Help
---

### Post by tiris on 2009-03-16
I am running the Eee remix of 8.04. I installed it in November 2008.

This has been working for me good for a while now.
It wasn't until I added a user that I have an issue.
And the issue is only on the new user's account.

It seems that somehow compiz is starting on the new user's account when the original account uses Metacity.

Both users don't have a  session file in the ~/.gnome2 dir so where is the difference? What other files make this behavior possible?

As a side note I know that I can replace compiz with metacity with this command.

```
metacity --replace
```
and then set it to restart in the gnome-session-properties command and save the session to startup in this manner. I know that this would make my troubles end, but where is the learning?

So anyone know where other configuration files are that would cause this behavior?


/usr/share/gnome/default.session
This file is for all users that don't have a session file in the user's gnome settings folder. There is not a session file for either user so this should not matter.

man gnome-wm talks about the windows manager being able to be set by each user by providing an environment variable WINDOW_MANAGER if this is the problem then the environment variable should be set for at least one of the users, but alas it is not set for either.

Also I read the post "The Great Desktop Effects FAQ of 2009" and the effects are set to none. In addition when I try and select one of the other effect options it tries switching out (to what I am not sure) then after some time displays an error message that it failed. Now after the message  it is in metacity - go figure, but it still starts in compiz after the user logs in.

To sum up the question is:
Where are the configuration files to alter this behavior (new user is starting up compiz instead of metacity)?

Any ideas are welcome, and I don't mind if you just point out some documentation that I should read on this matter.

---

