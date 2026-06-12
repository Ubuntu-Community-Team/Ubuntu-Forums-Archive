---
title: "Odd face browser problem"
date: 2007-05-07
forum: Desktop Environments
---

### Post by jamespetts on 2007-05-07
I am in the process of setting up two new computers running Ubuntu Feisty to go alongside two existing Windows XP computers in a home network, shared by three people. For ease of use, I use the face browser login on the Ubuntu computers. Also, to prevent me from having to configure everybody's user account twice on both of the Ubuntu machines, and to make sure that, once one user account is updated on one machine, it is automatically updated on the other, I cross-mounted the home directories.

By that, I mean that, of the two computers, kitchen and bedroom, and of the three users, james, robert and valerie, each will have a home directory in each. However, on bedroom, the home directories of valerie and robert are mounted over NFS from kitchen's /home/valerie and /home/robert directories, and vice versa for kitchen. (If somebody can work out a way of automating this process, Linux might be able to compete easily with the feature, codenamed "Castle", that was supposed to be in Windows Vista to create a peer-peer network that behaved in some respects like a domain network).

The problem is, however, that, even though I have set each user account to have an associated face, and set the login to the Ubuntu human face browser, the face icons that I chose for james on kitchen, and robert and valerie on bedroom (i.e., the users, in each case, whose home directories are mounted from the other computer) do not appear. I tried, as an experiment, unmounting the /home/james folder on kitchen, and specifying a face icon on the local /home/james profile, and it worked fine (but reverting back to the default face when re-mounted), so the problem is definitely related to mounting.

I should be most grateful for any ideas as to what to do about this problem: it is rather irritating having an incomplete set of faces.

---

### Post by metalheart on 2007-05-07
Where are those face images stored?

---

### Post by jamespetts on 2007-05-07
> **metalheart said:**
> Where are those face images stored?

/usr/share/pixmaps/faces . There is an identical copy of all three faces in the exact same location on both computers.

---

