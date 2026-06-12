---
title: "Cantor (Interface for Sage, Maxima and R)"
date: 2009-10-20
forum: Education &amp; Science
---

### Post by gunksta on 2009-10-20
I just saw this interesting post:

 [U][http://arieder.wordpress.com/2009/10/20/introducing-cantor/](http://arieder.wordpress.com/2009/10/20/introducing-cantor/)

[/U]It looks like KDE 4.4 (hopefully out in time for the next LTS) will include a KDE-based front-end for Sage, Maxima and R.

I thought Sage was a front-end too which doesn't make much sense to me, but assuming this announcement comes to fruition, this could be a useful tool.

I'm interested to see how the develop an interface that is flexible enough to handle multiple mathematics packages via a GUI. If it's nothing more than a glorified editor with pretty graphics output, it's not that interesting. If it's a genuine attempt to build a modular GUI to a diverse set of mathematics tools, thereby lowering the learning curve necessary to use them, this could be really really exciting.

---

### Post by shtumf on 2010-02-12
sage has a front-end notebook
after you install and run sage, you can type notebook() in the sage command shell or just run sage with sage --notebook
this will open a notebook in your favourite web browser. I realy like the idea of using a browser for a GUI. 
Cantor is also a cool app. I just wish cantor had same capabilities as sage notebook does. 

lets say in sage notebook I can do stuff like:
def nameoffunction(arguments):
.......if something:
.............do this
.......else:
.............do that

in cantor this is not posible, also identation is missing.

---

### Post by gunksta on 2010-02-12
You raise an interesting point of discussion.  While I am still looking forward to getting my hands on Cantor, I agree that Sage is an interesting product. 

In fact. It is a product that I have some questions about and since I'm the OP and you and I are the only two who have posted anything here, I think it's 100% OK to hijack this thread.  :popcorn:

Installation appears to be as simple as "sudo apt-get install sagemath". If I were to install sage, it would be on a laptop and this things get trucked all over creation. I'm looking at the dependencies and recommendations for sage and most of the deps I've already got covered although when I tried to install it breaks because it can't find an installation candidate for python-twisted (but this could be because of a couple of PPAs I have installed causing version conflicts, I'll have to check) 


[LIST=1]
[*]How hard is sage to set-up/administer? Once installed, do you have to create users, etc. Can I set up users if I want to?
[*]Since it's running via FireFox, it installs some sort of web-server or has one embedded in it. That's fine -- but is it always listening at a certain port? Again, because this thing travels and I work with a lot of private data (medicaid and records regarding children) I can NOT have a web-server port sitting wide open.  I would want to know either A) it only runs when I tell it to run or B) I can pass-lock it very easily and it's using a secure embedded server.    If necessary I could always just block it with iptables, but if it opens an unsecured port on my system, I may bypass it.
[*]Can I let other people on my network view what I am working on?  For example, can I develop something and give someone else a specific user-name/password which gives them access to the output, but not necessarily the ability to edit what I have created? This could be a neat collaborative tool.
[*]I saw on the Sage site that you can publish, via sage, some very nice graphics. That's nice, but I (sadly) deal with tables more often than graphics. Can I publish tables? I mean lots of ugly, complicated tables?
[*]shtumf -- is there any meaning to your handle? Just curious.
[/LIST]

I consider this thread to be thoroughly hijacked.   :D

---

### Post by shtumf on 2010-02-13
> How hard is sage to set-up/administer? Once installed, do you have to create users, etc. Can I set up users if I want to?Installing sage binary is easy.  If you want you can create users. You can disable login. You can enable or disable secure login. Ports can be configured. 

I use sage just for myself, unsecured and without login. So if you want help with administration you need to start reading here
[http://www.sagemath.org/](http://www.sagemath.org/)

I think you should try with the sage binary from sagemath.org
Or if you want you can also compile sage from source. 

Administration is possible via GUI
or you can to it from sage console

./sage 
help(notebook)

[I]Help on instance of NotebookObject in module sagenb.notebook.notebook_object:

class NotebookObject
 |  Start the Sage Notebook server. More documentation is available in the
 |  Sage installation guide, in the "Running the Sage Notebook Securely"
 |  chapter, and at [http://wiki.sagemath.org/StartingTheNotebook](http://wiki.sagemath.org/StartingTheNotebook).
 |
 |      INPUT:
 |
 |          - ``directory``     -- directory that contains the Sage notebook files;
 |            the default is .sage/sage_notebook, in your home directory.
 |          - ``[COLOR=Red]**port**[/COLOR]``          -- (default: 8000), port to serve the notebook on.
 |          - ``interface``     -- (default: 'localhost'), address of network
 |            interface to listen on; give '' to listen on all interfaces.
 |            You may use ``address`` here for backwards compatibility, but this
 |            is deprecated and will be removed in the future.
 |          - ``[COLOR=Red]**port_tries**[/COLOR]``    -- (default: 0), number of additional ports to try if
 |            the first one doesn't work (*not* implemented).
 |          - ``secure``        -- (default: False) if True use https so all
 |            communication, e.g., logins and passwords, between
 |            web browsers and the Sage notebook is encrypted
 |            via GNU TLS.  *Highly recommended!*
 |          - ``[COLOR=Red]**require_login**[/COLOR]`` -- (default: True) if True login is required else web
 |            user is automatically logged in as user admin.
 |          - ``**[COLOR=Red]reset[/COLOR]**``         -- (default: False) if True allows you to set the
 |            admin password.  Use this if you forget your admin
 |            password.
 |          - ``[COLOR=Red]**accounts**[/COLOR]``      -- (default: False) if True, any visitor to the
 |            website will be able to create a new account.  If
 |            False, only the admin can create accounts
 |            (currently, this can only be done by running with
 |            accounts=True for a few minutes, or on the command
 |            line with, e.g.,
 |
 |            ::
 |
 |                nb = load('./sage/sage_notebook/nb.sobj')
 |                nb.set_accounts(True)
 |                nb.add_user("username", "password", "email@place", "user")
 |                nb.save()
 |
 |          - ``open_viewer``   -- (default: True) whether to pop up a web browser.
 |            You can override the default browser by setting the
 |            SAGE_BROWSER environment variable, e.g., by putting
 |                export SAGE_BROWSER="firefox"
 |            in the file .bashrc in your home directory.
 |          - ``timeout``       -- (default: 0) seconds until idle worksheet
 |            sessions automatically timeout, i.e., the
 |            corresponding Sage session terminates. 0 means

[B][COLOR=Red]
EXAMPLES:[/COLOR][/B]
 |
 |      1. I just want to run the Sage notebook.  Type::
 |
 |             **[COLOR=Red]notebook()[/COLOR]**
 |
 |      2. I want to run the Sage notebook server on a remote machine and be the
 |         only person allowed to log in.  Type::
 |
 |             **[COLOR=Red]notebook(address='', secure=True)[/COLOR]**
 |
 |         the first time you do this you'll be prompted to set an administrator
 |         password.  Use this to login. NOTE: You may have to run
 |         notebook.setup() again and change the hostname.
 |
 |      3. I just want to run the server locally on my laptop and do not want to
 |         be bothered with having to log in::
 |
 |             [COLOR=Red]**notebook(require_login=False)**[/COLOR]
 |
 |         Use this ONLY if you are *absolutely certain* that you are the only
 |         user logged into the laptop and do not have to worry about somebody
 |         else using the Sage notebook on localhost and deleting your files.
 |
 |      4. I want to create a Sage notebook server that is open to anybody in
 |         the world to create new accounts. To run the Sage notebook publicly
 |         (1) at a minimum run it from a chroot jail or inside a virtual
 |         machine (see wiki.sagemath.org/StartingTheNotebook and the Sage
 |         install guide) and (2) use a command like::
 |
 |             notebook(address='', server_pool=['sage1@localhost'],
 |             ulimit='-v 500000', accounts=True)
 |
 |         The server_pool option specifies that worksheet processes run as a
 |         separate user.  The ulimit option restricts the memory available to
 |         each worksheet processes to 500MB.  See help on the `accounts' option
 |         above.
 |
 |         Be sure to make that the sage_notebook/nb.sobj and contents of
 |         sage_notebook/backups is chmod og-rwx, i.e., only readable by the
 |         notebook process, since otherwise any user can read nb.sobj, which
 |         contains user email addresses and account information (password are
 |         stored hashed, so fewer worries there). You will need to use the
 |         `directory' option to accomplish this.[/I]

---

### Post by shtumf on 2010-02-13
> Can I let other people on my network view what I am working on? For example, can I develop something and give someone else a specific user-name/password which gives them access to the output, but not necessarily the ability to edit what I have created? This could be a neat collaborative tool.Yes 
check this out [http://www.sagenb.org/pub/](http://www.sagenb.org/pub/)

> I saw on the Sage site that you can publish, via sage, some very nice graphics. That's nice, but I (sadly) deal with tables more often than graphics. Can I publish tables? I mean lots of ugly, complicated tables?I saw exaples where people use html for tables: 
[http://www.sagenb.org/home/pub/669/](http://www.sagenb.org/home/pub/669/)

maybe you can do it with latex
[http://www.sagenb.org/home/pub/1258/](http://www.sagenb.org/home/pub/1258/)

for tables check this [http://www.pytables.org](http://www.pytables.org)
maybe you can use pytables with sage somehow because both are python

Dont know realy...

> shtumf -- is there any meaning to your handle? Just curious.I have to finish 10 homeworks for Mathematical-physics-practicuum sort of a Numerical methods subject. I can use any program I want, Mathematica, Matlab ...or any programing language I want.
 
I like the idea: if you learn Sage you learn python too
Sage and tools used in sage are open-source
Rolling release, bugs fixed
I prefer to do stuff in Linux, I m using Kubuntu.
Sage has good documentation,examples, good community.

I have Cantor installed. I wanted to try it because one of its beckends is Sage.

---

### Post by gunksta on 2010-02-16
Interesting. Very Very interesting.

Thanks for the info!

---

