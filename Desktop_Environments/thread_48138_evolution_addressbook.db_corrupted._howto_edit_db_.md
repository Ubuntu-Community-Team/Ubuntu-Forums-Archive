---
title: "evolution addressbook.db corrupted. howto edit db file directly?"
date: 2005-07-11
forum: Desktop Environments
---

### Post by MarcDM on 2005-07-11
I was busy adding some photos to contacts I have in Evolution when I accidentally added a really big photo to a contact record. By really big I mean 1536x2048.

As soon as I clicked ok, the contact window froze up and CPU usage went straight up to 100%. And I had to killall evolution and evolution-data-server

Now, whenever I try to click on that contact, cpu usage goes to 100% immediately and Evolution stops responding to everything. I have to kill it.

I would like to know how I can use any tool to view/edit the addressbook.db file and just remove that record or the part of that contact record that's causing evolution to hang. 

Anyone got an idea? ](*,)

I tried to make use of python and pybsddb but the only database access I've ever used was SQL with c#. So the whole BerkeleyDB and pybsddb thing is tremendously confusing.

---

### Post by jeremy on 2005-07-11
A shot in the dark here;
Open evolution and select the contact just above (or below) the one with the large photo, then control + click the problem one, the press del to delete thereby deleting both.

---

### Post by MarcDM on 2005-07-11
tried it with 3 different views and same effect. Evolution just goes crazy once it touches the record with the large photo. A photo which has since been replaced by a much smaller one with the intention of getting Evolution to try using the smaller one instead.

I'm going back to experiment with pybsddb.

Thanks and keep thinking.

---

