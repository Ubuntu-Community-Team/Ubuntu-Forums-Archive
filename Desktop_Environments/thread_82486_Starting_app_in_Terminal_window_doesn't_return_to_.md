---
title: "Starting app in Terminal window doesn't return to prompt"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Leigh on 2005-10-26
In Hoary, when starting an application from the console prompt, e.g. GEDIT, the application would start but then I could carry on typing commands in the console.  Breezy doesn't seem to do this. It launches the application, but won't let me back to the command line until the running application is closed. If I type a CTRL-C at the command line, it closes the application.  Any idea how I can get back the Hoary functionality?

---

### Post by jrib on 2005-10-26
Type an ampersand at the end of your command.

For example, $gedit &

Note that if you close the console, your gedit will then close as well.

---

### Post by Leigh on 2005-10-27
Indeed, using the ampersand works, but I never used to do that in Hoary. Oh well.

Thanks for your help.

---

