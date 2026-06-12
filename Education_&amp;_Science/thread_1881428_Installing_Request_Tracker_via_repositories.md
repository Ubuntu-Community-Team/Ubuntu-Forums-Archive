---
title: "Installing Request Tracker via repositories"
date: 2011-11-15
forum: Education &amp; Science
---

### Post by itismike on 2011-11-15
Request Tracker by BestPractical.com is in the repositories, but after running through the installation dialogs it isn't live (127.0.0.1/rt returns 404.) 

There are wikis and forum threads on how to install RT from scratch, but since there is a repository package for it shouldn't there be steps to configure it after installation?

I found [this page]("https://help.ubuntu.com/community/RT") but it looks out-dated.

---

### Post by gordintoronto on 2011-11-15
What version of Ubuntu? The page you referenced is for a current version of Ubuntu, but there's a warning at the top. 

Are you running LAMP? Did you try running:
sudo dpkg-reconfigure request-tracker3.8

---

### Post by itismike on 2011-11-15
I'm using 10.04 LTS (desktop) and just re-ran the dpkg-reconfigure steps. I guess I don't really understand why it has to be done twice since I didn't deviate from the standard installation. The second time it failed performing the dbconfig-common step. I asked it to 'retry without reprompting for questions' and it apparently succeeded because it dumped me to the command-line. 

I'm also unsure about the use of MySQL in the documentation. The default choice during installation is SQLite3. Maybe I'll try it again choosing MySQL instead, but it seems like this system has had enough time to mature since the writing of that page to be able to use the default DB.

The errors I saw when re-running dpkg-reconfigure were:
> Couldn't finish 'schema' step.
> Error: Couldn't prepare SQL query:
CREATE TABLE Attachments(
...
)
ERROR: table Attachments already exists
> error encountered populating database:
...sqlite3 exited with non-zero status
dbconfig-common: request-tracker3.8 configure: trying again (skip questions).
dbconfig-common: writing config to ...request-tracker3.8.conf
user@host$

Thanks!

---

