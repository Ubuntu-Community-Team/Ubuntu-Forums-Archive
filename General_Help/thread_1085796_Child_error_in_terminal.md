---
title: "Child error in terminal"
date: 2009-03-03
forum: General Help
---

### Post by Optimus_Jazz on 2009-03-03
Hi guys, im having a problem with running my programs through gedit.
I have used this code to shortcut compile and run the program :

<code>
Compile:

#!/bin/bash
# Store the file name in a variable
echo "Compiling " $GEDIT_CURRENT_DOCUMENT_PATH
FILE_NAME=$GEDIT_CURRENT_DOCUMENT_NAME
# Check if file extension is .cpp
if [ `echo $FILE_NAME | cut -d "." -f 2` = "cpp" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 4`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
g++ -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
# Check if the file extension is c
if [ `echo $FILE_NAME | cut -d "." -f 2` = "c" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 2`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
gcc -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
exit 0


Running:

cat > runit.sh << datatag
#!/bin/bash
${GEDIT_CURRENT_DOCUMENT_NAME%.*}
read -p"Program finished. Press any key to exit..." -n1
datatag
chmod u+x runit.sh
gnome-terminal --command="runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}" 
</code>

This was working fine for me a few days ago but now when i want to run a simple test program the terminal opens with the error message "There was an error creating the child process for this terminal"

Anyone any ideas on what the problem is?

---

### Post by Optimus_Jazz on 2009-03-03
bump

still cant figure this out its driving me insane!

---

