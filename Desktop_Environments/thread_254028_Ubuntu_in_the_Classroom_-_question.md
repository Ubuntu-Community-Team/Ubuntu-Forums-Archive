---
title: "Ubuntu in the Classroom - question"
date: 2006-09-09
forum: Desktop Environments
---

### Post by ice_gamer on 2006-09-09
I am pretty adept as far as using Ubuntu/Linux goes, but have little experience in administration involving it.  Next week, I will be setting up 3-6 computers in my mom's classroom.  As the school system is poor and the children tend to download malware frequently, I have suggested installing Ubuntu on the systems, and everyone thinks that is an excellent idea.

Ok, here's the question.  I would like there to be a single student login (login name: student) for the students to login on.  They will have a password (probably: student) as well.  But when they try to install something, or access the administrator panels and such, I want that password to be different.  For example, if they go to system update or synaptic, I do not want them to be able to get into those using their student password.  That password to access those will be reserved for the teacher, who will never give it out to the students. :mrgreen: 

So how would I go about doing this?

---

### Post by Anonii on 2006-09-09
> **ice_gamer said:**
> I am pretty adept as far as using Ubuntu/Linux goes, but have little experience in administration involving it.  Next week, I will be setting up 3-6 computers in my mom's classroom.  As the school system is poor and the children tend to download malware frequently, I have suggested installing Ubuntu on the systems, and everyone thinks that is an excellent idea.

Ok, here's the question.  I would like there to be a single student login (login name: student) for the students to login on.  They will have a password (probably: student) as well.  But when they try to install something, or access the administrator panels and such, I want that password to be different.  For example, if they go to system update or synaptic, I do not want them to be able to get into those using their student password.  That password to access those will be reserved for the teacher, who will never give it out to the students. :mrgreen: 

So how would I go about doing this?
Why not give them automatic log in, and a root account for your mom?
Or just dont give the children any password/username and let your mom input them, they are just 3 PCs, it wont take that much time.

---

### Post by stormblue on 2006-09-09
I'm unsure of the correct way to get there in Ubuntu, as I don't use gnome, but there should be a "Users" or "Users and Groups" setting.  Open that up and and add a user.  You should be able to follow the prompt and it will allow to basically make a "guest" account where they can't really do anything.

---

### Post by ButteBlues on 2006-09-09
In the Users and Groups area of the system settings, just make sure that the student user isn't part of the Root or Sudo groups, and they should be limited to such a level that apt-get won't work for them, and they won't be able to modify any file outside of /home/student.

---

### Post by NetworkGuy on 2006-09-09
My suggestion is to install the computers normally with a ID/Password that is allowed to run sudo.  (The Teacher/Admin Account)

After that, through system --> Administration --> Users & Groups, create a new account as you described above.  That account (student) will not be able to run the administration commands.  Make sure the "Executing system administration tasks is unchecked under user privileges.

---

### Post by hellmet on 2006-09-09
yeah..it is as simple as that..
btw gud idea mate..of installing Ubuntu in the class..
Edubuntu??

---

### Post by ice_gamer on 2006-09-09
Well, this is a High School environment, so I think regular Ubuntu would be better.  Well, really they are the same thing, but the kids really dont need tuxtyping and tuxmath :D

Thankyou for the replies.  I think I'll go with the automatic login idea.

---

### Post by the_master on 2008-02-26
Wow I'm amazed this is literally word for word what i want to do in a classroom at my high school.  However i have a few problems,  One is i need Google earth to work under the student account and i installed it but its giving me a error and doesn't show the globe.  I can't post the error know since I'm at home, but i will tomorrow when i get to the computer.  Another is something i can't really control, but some of the repositories are blocked through the schools proxy server.  I have no idea why they would block them, or even how they know what they are.  If anyone can help that would be great, i'll be installing ubuntu on 15 computers and hope to spread knowledge of ubuntu to more classrooms.

Also if anyone knows anything else i can do to lock down the student account more it would help a lot.

---

