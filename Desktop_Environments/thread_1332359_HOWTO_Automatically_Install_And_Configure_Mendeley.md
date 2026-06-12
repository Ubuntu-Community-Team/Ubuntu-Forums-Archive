---
title: "HOWTO Automatically Install And Configure Mendeley Desktop"
date: 2009-11-20
forum: Desktop Environments
---

### Post by darkog on 2009-11-20
This script will automatically install and configure Mendeley Desktop for you on Ubuntu 9.10 and 9.04. You will still need to go to [http://www.mendeley.com/]("http://www.mendeley.com/") and register an account.

Copy and paste the code below into a new file. For example  medeley.sh.

Make the file executable
```
# sudo chmod +x mendeley.sh

```

Finally execute the file.
```
# sudo ./mendeley.sh

```

Full code below.
```

#!/bin/bash

# Name: mendeley_v2
#
# Author: darkog
#
# Date: Nov 19, 2009
#
# Purpose:
# This script will automatically install and
# configure the Mendeley academic desktop software.
#
# Notes:
# This script was tested to run on Ubuntu 9.10 x86.
#
# Return codes:
# None
#
########################################################

# --------------------------------------------
# Backup your apt sources.list file.
# --------------------------------------------
today=$(date '+%m-%d-%Y')
cp /etc/apt/sources.list /etc/apt/sources.list_$today

# --------------------------------------------
# Add the Mendeley Ubuntu 9.04 repositories.
# If you use a different distro, you can go to
# http://www.mendeley.com/repositories
# and change the section as needed. Follow the
# format below.
# --------------------------------------------
echo "deb http://www.mendeley.com/repositories/xUbuntu_9.04 /" >> /etc/apt/sources.list

# --------------------------------------------
# Update & refresh your apt sources
# --------------------------------------------
apt-get update

# --------------------------------------------
# Install and auto configure the Mendeley
# software. Unfortunately the Mendeley team
# did not have an easily available .asc file
# which i could use with gpg for SecureApt.
# If they ever put one up, please contact me
# and perhaps I can add the functionality to
# import the keys into this script. For now
# I just have to force the install and trust
# that their files are not compromised.
# --------------------------------------------
apt-get install mendeleydesktop -y --force-yes

exit 0

```

---

