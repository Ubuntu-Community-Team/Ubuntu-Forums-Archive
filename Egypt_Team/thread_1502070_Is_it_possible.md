---
title: "Is it possible ??"
date: 2010-06-05
forum: Egypt Team
---

### Post by mustafa atta on 2010-06-05
hello
i have a free space in the primary partion (unlocated) i want to add it to my extended partion does it possible or it's just crazy talk
please if it possible tell me how and if not give me another solution 
thanks in advance

---

### Post by sites on 2010-06-05
What?  Merging unlocated partitions?  That's just crazy talk!

---

### Post by mustafa atta on 2010-06-05
i didn't understand
i don't want to merge 
i resized my primary partion to extract 15 gb free to add them to the extended partion but when i tried that with gparted it didn't work that's it

---

### Post by sites on 2010-06-05
Sorry man.. I was just joking, because you said the partition was "unlocated" when you meant to say "unallocated".

Follow [this link]("http://www.howtoforge.com/linux_resizing_ext3_partitions").  It's old, but should give you some ideas to point you in the right direction.

---

### Post by thebigob on 2010-06-05
If you want to do this with a graphical user interface GParted is the application you are looking for.

---

### Post by mustafa atta on 2010-06-05
> **thebigob said:**
> If you want to do this with a graphical user interface GParted is the application you are looking for.

exactly i want that but i can't i tried with g parted but it doesn't work please help me and tell me how
when i tried to make new partion in this space the only option available is primary and the other options ( extended and logical )are dis-active 
what shall i do ?

---

### Post by prshah on 2010-06-05
> **mustafa atta said:**
> when i tried to make new partion in this space the only option available is primary and the other options ( extended and logical )are dis-active 

When partitioning, you should be aware that you can have only 4 partitions. One (and only one) of these can be an extended partition, which can in turn contain several (128?) logical partitions (or "logical drives" in Win parlance)

If you want to merge your unallocated space into your extended partition, you will need to boot off the live CD, then unmount any active partitions, and then merge the unallocated space into the extended partition. 

You will then have to (again) merge the unallocated space to one of the logical partitions.

Post back if you want more details.

---

### Post by mustafa atta on 2010-06-05
> **prshah said:**
> When partitioning, you should be aware that you can have only 4 partitions. One (and only one) of these can be an extended partition, which can in turn contain several (128?) logical partitions (or "logical drives" in Win parlance)

If you want to merge your unallocated space into your extended partition, you will need to boot off the live CD, then unmount any active partitions, and then merge the unallocated space into the extended partition. 

You will then have to (again) merge the unallocated space to one of the logical partitions.

Post back if you want more details.
thank alot 
i know that about extended and primary but i don't know about live cd i will try and come back

---

### Post by mustafa atta on 2010-06-05
> **mustafa atta said:**
> thank alot 
i know that about extended and primary but i don't know about live cd i will try and come back
it dosn't work again i tried from live cd and i found all drives is unmounted but also as it is the logical partion option is still disable and there is no merge tool i found ?
please help me asap

---

### Post by prshah on 2010-06-05
> **mustafa atta said:**
> no merge tool i found ?

You need to use the resize option. There is no "merge" option.

---

### Post by mustafa atta on 2010-06-05
> **prshah said:**
> You need to use the resize option. There is no "merge" option.
i've already used it but it dosn't work
after seprating the 15 gb i can't add them to any logical partion ?

---

### Post by thebigob on 2010-06-05
Maybe something like this will help:

[http://www.youtube.com/watch?v=WU9KY5DObDA](http://www.youtube.com/watch?v=WU9KY5DObDA)

---

### Post by Sensiva on 2010-06-05
Mustafa, You need to understand the partitioning mechanism and structure. Commonly there are two partitions in a harddrive, one as a **Primary** that has the OS boot (active) and the other partition is called **Extended** partition, which _**CONTAINS**_ sub partitions that we call **Logical **partition.

Attached an example layout of 250GB partitions, /dev/sda1 is a **Primary** partition and /dev/sda2 is an **Extended** partition (indicated in **[COLOR=Red]red[/COLOR]**) that _**CONTAINS**_ all Logical partitions starting from /dev/sda5 to /dev/sda15. This layout will give you a clear figure of the difference between **Primary**, **Extended** and **Logical** partitions.

P.S. Colors will be different when using GParted LiveCD.

What I understand from your description is that you resized the **Primary** partition to a smaller size, which resulted of 15GB of unallocated space, and you need to use those 15GB as a new partition or add them as free space to one of the already existing **Logical **partitions**. _So I will assume you need to do one of the following:_**


[LIST]
[*]Using the unallocated 15GB as a new **Primary** partition. [COLOR=Red]**(Recommended)**[/COLOR]
[/LIST]
[INDENT]In this case use GParted in Ubuntu or LiveCD and right click the unallocated space and create a new **Primary** partition. This won't take more than few seconds to get it done unlike the next two cases
[/INDENT]
[LIST]
[*]Using the unallocated 15GB as a new **Logical** partition partition.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended** partition to fill the whole unallocated space, in other words move the unallocated 15GB space into the **Extended **partition. Then right click the unallocated space and create a new** Logical** partition. 
[/INDENT]
[LIST]
[*]Add the unallocated 15GB as a free space to one of the already existing **Logical** partitions.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended**  partition to fill the whole unallocated space, in other words move the  unallocated 15GB space into the **Extended **partition. Then move the **Logical** partitions as necessary to make the unallocated 15GB space on the[COLOR=Red]** RIGHT **[/COLOR]of the partition to be grown. Having all this done, now you may right click on that partition and resize it to fill all the unallocated space.
[/INDENT]Note that the last two cases will be VERY lengthy and if power went down you will weep  like a baby for weeks for the lost data. so make sure battery is full and charger is always connected if its a notebook.

I hope this post helps you, Try to pay attention as much as possible to provide any useful info in case things went wrong, in such case I advice you calling any of the LoCo team members to help you in recovering ASAP.

Call me. If I am not available, you may try calling any of the available supporting members in this list [https://wiki.ubuntu.com/EgyptTeam/Members](https://wiki.ubuntu.com/EgyptTeam/Members)
 
Good Luck! :D
/Sensiva>

---

### Post by mustafa atta on 2010-06-05
> **Sensiva said:**
> Mustafa, You need to understand the partitioning mechanism and structure. Commonly there are two partitions in a harddrive, one as a **Primary** that has the OS boot (active) and the other partition is called **Extended** partition, which _**CONTAINS**_ sub partitions that we call **Logical **partition.

Attached an example layout of 250GB partitions, /dev/sda1 is a **Primary** partition and /dev/sda2 is an **Extended** partition (indicated in **[COLOR=Red]red[/COLOR]**) that _**CONTAINS**_ all Logical partitions starting from /dev/sda5 to /dev/sda15. This layout will give you a clear figure of the difference between **Primary**, **Extended** and **Logical** partitions.

P.S. Colors will be different when using GParted LiveCD.

What I understand from your description is that you resized the **Primary** partition to a smaller size, which resulted of 15GB of unallocated space, and you need to use those 15GB as a new partition or add them as free space to one of the already existing **Logical **partitions**. _So I will assume you need to do one of the following:_**


[LIST]
[*]Using the unallocated 15GB as a new **Primary** partition. [COLOR=Red]**(Recommended)**[/COLOR]
[/LIST]
[INDENT]In this case use GParted in Ubuntu or LiveCD and right click the unallocated space and create a new **Primary** partition. This won't take more than few seconds to get it done unlike the next two cases
[/INDENT]
[LIST]
[*]Using the unallocated 15GB as a new **Logical** partition partition.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended** partition to fill the whole unallocated space, in other words move the unallocated 15GB space into the **Extended **partition. Then right click the unallocated space and create a new** Logical** partition. 
[/INDENT]
[LIST]
[*]Add the unallocated 15GB as a free space to one of the already existing **Logical** partitions.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended**  partition to fill the whole unallocated space, in other words move the  unallocated 15GB space into the **Extended **partition. Then move the **Logical** partitions as necessary to make the unallocated 15GB space on the[COLOR=Red]** RIGHT **[/COLOR]of the partition to be grown. Having all this done, now you may right click on that partition and resize it to fill all the unallocated space.
[/INDENT]Note that the last two cases will be VERY lengthy and if power went down you will weep  like a baby for weeks for the lost data. so make sure battery is full and charger is always connected if its a notebook.

I hope this post helps you, Try to pay attention as much as possible to provide any useful info in case things went wrong, in such case I advice you calling any of the LoCo team members to help you in recovering ASAP.

Call me. If I am not available, you may try calling any of the available supporting members in this list [https://wiki.ubuntu.com/EgyptTeam/Members](https://wiki.ubuntu.com/EgyptTeam/Members)
 
Good Luck! :D
/Sensiva>
thanks alot sensiva
but there is a very important question
how to move the unallocated space into extended partion in the rwo cases ??

---

### Post by mustafa atta on 2010-06-05
> **Sensiva said:**
> Mustafa, You need to understand the partitioning mechanism and structure. Commonly there are two partitions in a harddrive, one as a **Primary** that has the OS boot (active) and the other partition is called **Extended** partition, which _**CONTAINS**_ sub partitions that we call **Logical **partition.

Attached an example layout of 250GB partitions, /dev/sda1 is a **Primary** partition and /dev/sda2 is an **Extended** partition (indicated in **[COLOR=Red]red[/COLOR]**) that _**CONTAINS**_ all Logical partitions starting from /dev/sda5 to /dev/sda15. This layout will give you a clear figure of the difference between **Primary**, **Extended** and **Logical** partitions.

P.S. Colors will be different when using GParted LiveCD.

What I understand from your description is that you resized the **Primary** partition to a smaller size, which resulted of 15GB of unallocated space, and you need to use those 15GB as a new partition or add them as free space to one of the already existing **Logical **partitions**. _So I will assume you need to do one of the following:_**


[LIST]
[*]Using the unallocated 15GB as a new **Primary** partition. [COLOR=Red]**(Recommended)**[/COLOR]
[/LIST]
[INDENT]In this case use GParted in Ubuntu or LiveCD and right click the unallocated space and create a new **Primary** partition. This won't take more than few seconds to get it done unlike the next two cases
[/INDENT]
[LIST]
[*]Using the unallocated 15GB as a new **Logical** partition partition.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended** partition to fill the whole unallocated space, in other words move the unallocated 15GB space into the **Extended **partition. Then right click the unallocated space and create a new** Logical** partition. 
[/INDENT]
[LIST]
[*]Add the unallocated 15GB as a free space to one of the already existing **Logical** partitions.
[/LIST]
[INDENT]In this case you must use GParted LiveCD to resize the **Extended**  partition to fill the whole unallocated space, in other words move the  unallocated 15GB space into the **Extended **partition. Then move the **Logical** partitions as necessary to make the unallocated 15GB space on the[COLOR=Red]** RIGHT **[/COLOR]of the partition to be grown. Having all this done, now you may right click on that partition and resize it to fill all the unallocated space.
[/INDENT]Note that the last two cases will be VERY lengthy and if power went down you will weep  like a baby for weeks for the lost data. so make sure battery is full and charger is always connected if its a notebook.

I hope this post helps you, Try to pay attention as much as possible to provide any useful info in case things went wrong, in such case I advice you calling any of the LoCo team members to help you in recovering ASAP.

Call me. If I am not available, you may try calling any of the available supporting members in this list [https://wiki.ubuntu.com/EgyptTeam/Members](https://wiki.ubuntu.com/EgyptTeam/Members)
 
Good Luck! :D
/Sensiva>
thanks alot sensiva
but there is a very important question
how to move the unallocated space into extended partion in the  last two cases ??

---

### Post by mustafa atta on 2010-06-05
> **Sensiva said:**
> 

[INDENT]In this case you must use GParted LiveCD to resize the **Extended**  partition to fill the whole unallocated space, in other words move the  unallocated 15GB space into the **Extended **partition. Then move the **Logical** partitions as necessary to make the unallocated 15GB space on the[COLOR=Red]** RIGHT **[/COLOR]of the partition to be grown.
/Sensiva>

How exactly i do that ??

---

### Post by Sensiva on 2010-06-05
> **mustafa atta said:**
> How exactly i do that ??

In GParted LiveCD right click the **Extended** partition then choose _Resize/Move_, it will pop up another dialogue showing the whole **Extended** partition. Drag the slider to the _**LEFT**_. This will enlarge (grow) the **Extended** partition to fill the unallocated 15GB free space.

---

