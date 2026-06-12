---
title: "mailman help please"
date: 2009-03-29
forum: General Help
---

### Post by BobbyS on 2009-03-29
Hello,

I am trying to install mailman from the mailman site install page and have run into a question if someone can help. I added a group like the instructions say but I can't add the user. I put this in:

useradd -c''GNU Mailman'' -s /no/shell -d /no/home -g mailman mailman

but then I get this:

bobby@gman:~$ useradd -c''GNU Mailman'' -s /no/shell -d /no/home -g mailman mailman
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -l,                           do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create home directory for the new user
                                account
  -N, --no-user-group           do not create a group with the same name as


Am I supposed to add something else or what?



Thanks for any help!
BobbyS

---

### Post by merlinv12 on 2009-04-22
You are getting that problem because your useradd does not have the -s option so it is not processing your request

---

