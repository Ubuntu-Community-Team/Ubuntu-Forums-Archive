---
title: "how to compile scilab 4.0 from source?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by forbmj on 2006-02-22
after reading the README_Unix, I did:

./configure
sudo make install

but after the following output, nothing is really compiled. I don't know why.

tar: pvm3/lib/LINUX/pvmd3: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
tar: pvm3/lib/LINUX/pvmgs: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
tar: pvm3/lib/LINUX/pvm: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
tar: pvm3/bin/LINUX/*: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
make[1]: Entering directory `/usr/local/scilab/lib/scilab-4.0'
creating Path.incl SCIDIR=/usr/local/scilab/lib/scilab-4.0
make[2]: Entering directory `/usr/local/scilab/lib/scilab-4.0/scripts'
../bin/scilab created
../bin/Blatexpr created
../bin/Blatexpr2 created
../bin/Blatexprs created
../bin/Blpr created
../bin/BEpsf created
../util/Blatdoc created
../util/Blatdocs created
make[2]: Leaving directory `/usr/local/scilab/lib/scilab-4.0/scripts'
strip: 'bin/scilex': No such file
make[1]: Leaving directory `/usr/local/scilab/lib/scilab-4.0'
install -d /usr/local/scilab/share/doc/scilab-4.0/
install ACKNOWLEDGEMENTS CHANGES README_Unix Version.incl \
        licence.txt license.txt  /usr/local/scilab/share/doc/scilab-4.0
install -d /usr/local/scilab/bin
rm -f  /usr/local/scilab/bin/scilab
ln -fs /usr/local/scilab/lib/scilab-4.0/bin/scilab /usr/local/scilab/bin/scilab
rm -f  /usr/local/scilab/bin/intersci
ln -fs /usr/local/scilab/lib/scilab-4.0/bin/intersci /usr/local/scilab/bin/intersci
rm -f  /usr/local/scilab/bin/intersci-n
ln -fs /usr/local/scilab/lib/scilab-4.0/bin/intersci-n /usr/local/scilab/bin/intersci-n

---

### Post by shakespeare on 2006-07-02
The command sequence should be:

./configure
make all
sudo make install

If the configure step gives any error messages, then some required packages are missing. They should be installed and the configure must then be repeated. All dependencies must be satisfied before proceeding to the make step.

---

