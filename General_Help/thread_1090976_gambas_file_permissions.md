---
title: "gambas file permissions"
date: 2009-03-08
forum: General Help
---

### Post by rick71 on 2009-03-08
I would like to use Gambas to create an app that will allow me to change file permissions by picking selecting the files from a predefined list.

Can anyone point me to some docs, or show me how to do this?

Any and all help appreciated.

---

### Post by SteveDee on 2009-03-09
> **rick71 said:**
> I would like to use Gambas to create an app that will allow me to change file permissions by picking selecting the files from a predefined list.

Can anyone point me to some docs, or show me how to do this?

Any and all help appreciated.

I'm assuming that you are familiar with Gambas, and you just want a way of changing file permissions from Gambas.

I've just tried using "Exec" to run chmod and this seems to work. So as a starting point try this:-
Start a new Gambas project and add 3 buttons and a TextArea control.

Add this code to FMain:-
  PUBLIC SUB Button1_Click()
    EXEC ["ls", "-l", Application.Path] TO TextArea1.Text
  END

  PUBLIC SUB Button2_Click()
    EXEC ["chmod", "ug+w", Application.Path & "/Test"]
  END

  PUBLIC SUB Button3_Click()
    EXEC ["chmod", "ug-w", Application.Path & "/Test"]
  END

Create a file in this project folder called "Test"

Now run the code and see the effect on Test.

I hope this helps.

---

### Post by rick71 on 2009-03-10
Thanks for the reply.
I am not familiar with Gambas. This is my first project, and I haven't worked in BASIC for 25 years.

What I want to do is change the file permissions on a list of files that I have selected from a check box list.

It looks like I have to use an EXEC command for each file inside PUBLIC SUB Button2_Click()routine.

Now I just have to figure out how to assign variables from check boxes and get them into if-then statements.

Thanks again for the info.

---

### Post by rick71 on 2009-03-10
Thanks for the reply.
I am not familiar with Gambas. This is my first project, and I haven't worked in BASIC for 25 years.

What I want to do is change the file permissions on a list of files that I have selected from a check box list.

It looks like I have to use an EXEC command for each file inside PUBLIC SUB Button2_Click()routine.

Now I just have to figure out how to assign variables from check boxes and get them into if-then statements.

Thanks again for the info.

---

### Post by rick71 on 2009-03-10
Thr following works fine:
PUBLIC SUB Button2_Click()
EXEC ["chmod", "ugo-w", Application.Path & "/Test"]
END


This next section doesn't work:

PUBLIC SUB Button2_Click()
IF CheckBox1.Value = TRUE THEN
EXEC ["chmod", "ugo-w", Application.Path & "/Test"]
ENDIF 
END

What am I doing wrong?

EDIT!!!
Nevermind... I found the mistake. I wasn't matching the script to the actual button. The IF/THEN now works.

---

### Post by SteveDee on 2009-03-11
> **rick71 said:**
> Thanks for the reply.
I am not familiar with Gambas. This is my first project, and I haven't worked in BASIC for 25 years....



It looks like you are making good progress.

Documentation for Gambas is rather patchy, but here are some links you may find useful:-
Gambas 2 Doc; [http://gambasdoc.org/help/](http://gambasdoc.org/help/)
Gambas Wikibook; [http://en.wikibooks.org/wiki/Gambas](http://en.wikibooks.org/wiki/Gambas)
Tutorial: [http://kalaharix.wordpress.com/gambas/gambas-28-on-ubuntu-804/](http://kalaharix.wordpress.com/gambas/gambas-28-on-ubuntu-804/)
Tutorial: [http://davidasorey.net/static/gambas-tutorial/gambas_tutorial_en.html](http://davidasorey.net/static/gambas-tutorial/gambas_tutorial_en.html)

Apart from this forum, you can also get help from these:-
[http://www.linuxbasic.net/index.php?board=3.0](http://www.linuxbasic.net/index.php?board=3.0)
[http://forum.stormweb.no/index.php](http://forum.stormweb.no/index.php)
[http://www.nabble.com/gambas-user-f3427.html](http://www.nabble.com/gambas-user-f3427.html)

---

### Post by rick71 on 2009-03-13
Thanks. I'll take a look at those.

---

### Post by rick71 on 2009-03-13
Ok.. I'm stuck again. I am trying to change others read permissions on several files on a web server. my account is the owner. I can change the permissions on a file in the project folder (thanks for that), but not in www. However, I can run a shell script from my user account to change the permissions.

Here is the Gambas code:
PUBLIC SUB Button1_Click()
 EXEC ["chmod", "o+r", "/var/www/tests.html"]
END

Eventually there will be about 60 IF/THEN statements working on files from a check list. For now I just want to get it to work on one file.

Any/all help appreciated.

---

### Post by SteveDee on 2009-03-14
> **rick71 said:**
> Ok.. I'm stuck again. I am trying to change others read permissions on several files on a web server. my account is the owner. I can change the permissions on a file in the project folder (thanks for that), but not in www. However, I can run a shell script from my user account to change the permissions.

Here is the Gambas code:
PUBLIC SUB Button1_Click()
 EXEC ["chmod", "o+r", "/var/www/tests.html"]
END

Eventually there will be about 60 IF/THEN statements working on files from a check list. For now I just want to get it to work on one file.

Any/all help appreciated.

What you do next depends upon whether you have the Gambas IDE installed on the machine you are using as a web server.

If you do, then you should run your application again from the IDE and see if you have any messages in the IDE Console tab. As an example I set my "Test" file owner to 'root' and then ran the program. The attached file shows the resulting message. 

If you can only run the executable, then you need to add an error handler to your code to display error messages.

I suspect you have some kind of Permissions problem with your Permissions program.

---

### Post by rick71 on 2009-03-15
I have no idea what is going on. Sometimes things work, and then they stop.

If I make changes to the EXEC statements you suggested, iusing o-r or o+r, things stop working, and changing them back doesn't get them working again. And nothing ever shows in the console.

 Ah, well.

At least I have a shell script I cam use until I figure this out.

.. and thanks for your help.

---

### Post by rick71 on 2009-03-18
It seems I can now use my Gambas app to change the permissions as I was trying to do. I a not sure why it is working now. I did make sure the button were opening and closing what I wanted them to, and I made sure all the files I wanted to change were owned by me.

... and now it seems to work.

Thanks.

---

