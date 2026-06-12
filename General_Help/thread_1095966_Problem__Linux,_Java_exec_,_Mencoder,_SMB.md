---
title: "Problem : Linux, Java exec , Mencoder, SMB"
date: 2009-03-14
forum: General Help
---

### Post by ymark on 2009-03-14
Hello all,



Please help me out. I have a problem 

- I use a Ubuntu Linux 8.10

- I have a mount point to a SMB location :

 > /mnt/STORAGE/

- I'm trying to execute a mencoder command from Java like this :
  > Process process = Runtime.getRuntime().exec(cm);

- An example of mencoder command :

> /usr/local/bin/mencoder -oac mp3lame  -o "/mnt/STORAGE/OUT/myfile2.flv"   -ovc vfw -xvfwopts codec=vp6vfw.dll:compdata=aaaaonepass.mcf -lameopts cbr:br=128 -vf flip,scale=320:240 -af lavcresample=22050 -of lavf   "/mnt/STORAGE/IN/file2.mkv"


-Running this mencoder command from the console it works perfectly.

-Running this command from JAVA exec i've got this error from mencoder output :

> File not found: '"/mnt/STORAGE/IN/file2.mkv"'



It seems that when i run this command from java it does not recognize the SMB.

I need to add some refferences or i need to add permisions??
I'm running this java program with root


Please help me out...


Thank you,
ymark

---

### Post by ymark on 2009-03-15
Hello all,




I didn't managed to figure out the problem but i managed to get around


because directly executing the mencoder i don't have acces to the smb mount point i've created a script with the command and executed with bash :


```
 if (new File("/bin/bash").exists()) {

                File script = new File("script.sh");
                try {
                    FileWriter fstream = new FileWriter(script);
                    BufferedWriter out = new BufferedWriter(fstream);
                    out.write("#! /bin/bash\n");
                    out.write(cm);
                    out.close();
                    fstream.close();

                    cm = "/bin/bash script.sh";
                } catch (Exception e) {
                    System.err.println("Error: " + e.getMessage());
                }
            }
 Process process = Runtime.getRuntime().exec(cm);

```


Checking that "/bin/bash" exists makes this compatible with windows too


Thank you,
Ymark

---

