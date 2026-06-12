---
title: "How to run a python file from URL of a browser"
date: 2009-01-23
forum: General Help
---

### Post by ravikonam on 2009-01-23
I am unable to run a python file from URL of a browser.
I tried http://localhost:8000/<appname>/test.py, which given 404 error.

Any one, please help me how can I run a .py file from a browser.

---

### Post by Christmas on 2009-01-23
Try with port 80?

---

### Post by ravikonam on 2009-01-23
No. I am using Django as a cms and it is running on 8000.
my whole project is running on this port.

The problem here is, I need to execute the file [http://localhost:8000/demo/test.py](http://localhost:8000/demo/test.py) from a html.

Please help me.

---

### Post by Christmas on 2009-01-23
Never used, although I tried it now and it seems to work (I get the welcome to django message on localhost:8000). Can't help you much since I don't know how cms work, but please read the documentation on their official website [here]("http://docs.djangoproject.com/en/dev/intro/tutorial01/#intro-tutorial01"). And all the other documents, it surely explains there how to do it. Good luck!

---

### Post by ravikonam on 2009-01-23
Thanks for quick reply.
Plz ignore Djang & cms. 


I created a file (test.py with some text) and placed it in the application (demo) of django and tried to run it from browser as [http://localhost:8000/demo/test.py](http://localhost:8000/demo/test.py), which is a 404.

Can u please let me know how u ran your file, 
which server you have used and where did you plzce the file.

---

### Post by hyper_ch on 2009-01-23
did you install and enable libapache2_mod_python? Might be called differently but I tend to think you use apache as webserver and it needs to have that module...

---

### Post by .Maleficus. on 2009-01-23
Did you make sure to have a regex pattern for that address in urls.py?  And that the app has been installed in INSTALLED_APPS?  What's the 404 you're getting?  If you can't answer those questions, post your urls.py, settings.py and the yellow part of the 404.


Edit:  Also, you are running the Django development server, right?  When you get a 404, make sure you read it carefully.  It has really useful information in it and makes tracking down errors much easier than blindly looking through files.

---

### Post by ravikonam on 2009-01-23
The below is the error in the browser:
------------
Page not found (404)
Request Method: GET 
Request URL: [http://localhost:8000/pilot/test.py/](http://localhost:8000/pilot/test.py/) 
------------

please find the attached zip has settings.py and urls.py files.
Application name is 'pilot' and Project is 'natgeo'.
I verified INSTALLED_APPS is proper.

please verify and let me know if I miss anything.

---

### Post by .Maleficus. on 2009-01-23
If I read urls.py correctly, you don't have a view (or URL in that matter) pointing to '/pilot/test'.  The regex you'd want to use is " r'^pilot/test/$' " and you then need to map a view to it.  Do your other URLs work, like /pilot/start?  What exactly do you mean you want to execute test.py?

---

### Post by ravikonam on 2009-01-23
Maleficus,

Thanks for quick reply.

Other URLs like /pilot/start working properly.
I just added the below entry to urls.py 
(r'^pilot/test/$', 'natgeo.pilot.test.py'), 
!--- I think .py should be removed. I tried that too.

but still the error is same.

Actually what I need is: from a html I have to call [http://localhost:8000/pilot/test.py](http://localhost:8000/pilot/test.py), which will generate an XML and the xml is input to a flash file.

my question is how can we run the test.py file from a html or from a URL in a browser? 
for ex, I run a jsp (test.jsp) file from a browser as [http://localhost:8000/pilot/test.jsp](http://localhost:8000/pilot/test.jsp), which will generate some output.

please help me.

---

### Post by ravikonam on 2009-01-27
can any one, please help me on this?

---

