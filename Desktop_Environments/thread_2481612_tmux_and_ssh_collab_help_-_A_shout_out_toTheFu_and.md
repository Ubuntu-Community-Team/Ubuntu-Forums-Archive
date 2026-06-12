---
title: "tmux and ssh collab help - A shout out toTheFu and Morbius1 for all their support"
date: 2022-12-04
forum: Desktop Environments
---

### Post by mike430 on 2022-12-04
Almost done here for what I'm trying to accomplish. 

In short, trying to get a basic collaborative learning environment for a 13 and 9 year old as well as myself, I am still learning. 

Using samba, ssh, and tmux, for our environment. Using samba in lieu of NFS due to dual operating systems on my boys machines.

Samba - check
ssh - check
tmux - help needed.

My question, when myself and another user are ssh'd into a third server machine cannot recognize either tmux session.

ssh works fine for all users and I have done a 'sudo apt install tmux' only on the server machine. No special configuration has been made per tmux, except on the server I did change the tmux config file to use 'ctrl a' as opposed to 'ctrl b' for certain command input. This configuration is set on the server and performed by myself 'vcandy'. Further, independently all users can access tmux but cannot connect to each other's sessions. The sessions for each other do not appear to exist.

Thanks, Mike

---

### Post by ActionParsnip on 2022-12-05
Does screen work OK? Just to test

---

### Post by mike430 on 2022-12-05
Yes.

Can't figure how to split panes and have 2 separate users?

tmux new -s user1
tmux new -s user2 -t user1

tmux ls - confirms (group user1) is attached

There's only so many commands on this thing. Should be able to get this but I'm not...

---

### Post by mike430 on 2022-12-05
Ok, almost there with this. 

Got the independent windows to work. The shared socket in the /tmp folder needs a group all users are part of. The group, however, changes to the user group that first initiates a new session. Thus, the group needs to be changed after new session is started. I looked at 3 or 4 examples online, this wasn't clear in any of 'em. 

The next question relates to this same environment. The independent windows only allow one of the attached session users to be active at any given time. Isn't there a way that all users can be active independently at the same time?

---

### Post by mike430 on 2022-12-06
I don't think tmux & ssh is going to provide the last part I am looking for. Although you can, as in my case, have 3 users using 3 panes and all have independent access the limitation is, is that only one person can type at once and when another wants there turn they have to toggle to their pane.

I just tested Google Meets and does exactly what I want it to do for what we are trying to accomplish. The solution was right under my nose the entire time. Ha!

With using Google Meets presents another issue, the dreaded Video Card Driver issue! My video is grainy and slow and I am usinig rtx 3080..

---

