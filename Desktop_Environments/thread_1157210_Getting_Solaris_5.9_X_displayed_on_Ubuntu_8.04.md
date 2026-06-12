---
title: "Getting Solaris 5.9 X displayed on Ubuntu 8.04"
date: 2009-05-12
forum: Desktop Environments
---

### Post by PaulHuffman on 2009-05-12
Yesterday I had to log in remotely back on my old Solaris box.  I thought my Ubuntu desktop would easily allow me to display X windows from Solaris but I couldn't figure it out. Luckily I still had Reflection X set up on a Windows PC and I was able to make that work. But why can't I get it to work with Ubuntu desktop?  All I can get back from Solaris is "Can't open display: 161.217.*.*:0"

What I've tried is logging into Solaris with Konsole and ssh, in a C shell on Solaris "setenv DISPLAY ubuntu's IP:0.0" and "xhosts + pauleseries" since the Solaris /etc/hosts file has pauleseries IP address already in it. pauleseries is the name of the ubuntu desktop But when I try the xhost command on Solaris or try a test X app like xclock&, I get the "Can't open display" error.

Do I need to do something on the Ubuntu side with xauth?

---

### Post by apmcd47 on 2009-05-12
[LIST=1]
[*]Use ssh -X to enable X-forwarding
[*]Don't set DISPLAY on the sun - it should be set by default to a pseudo display
[/LIST]
Basically ssh allows X Server tunnelling (or X forwarding), so that you don't need to worry about setting the display back to your machine, or figure out the security (eg xauth). However OpenSSH disables X forwarding by default.

You can enable X forwarding on a host by host basis or for all hosts by setting up the ~/.ssh/config file.

Andrew

---

### Post by PaulHuffman on 2009-05-12
Nope, still getting "Can't open display".  Tried setenv DISPLAY also, but got the same thing.

---

### Post by apmcd47 on 2009-05-13
> **PaulHuffman said:**
> Nope, still getting "Can't open display".  Tried setenv DISPLAY also, but got the same thing.

What was DISPLAY set to immediately after login? It should be something like *localhost:11.0* Do you have a command in your .login/.cshrc files to set the display? I assume you use csh if you use the setenv command.

---

### Post by PaulHuffman on 2009-05-13
DISPLAY is not set when I first ssh in. Using csh.

---

### Post by apmcd47 on 2009-05-13
Okay, try this:
```

Host *
   ForwardX11 yes

```
Put that in a file called ~/.ssh/config on the Ubuntu (I assume you don't have one) and try again. Just log in and see what DISPLAY is set to.


You may also need to check /etc/ssh/sshd_config on the Solaris box for the values of *X11Forwarding* and *X11UseLocalhost*. If *X11Forwarding* is set to *no* you may need to the Solaris SysAdmin to change it to *yes*.

Andrew

---

### Post by PaulHuffman on 2009-05-13
I'm the sysadmin of the Solaris box. But I was able to talk myself into trying this.  

Made the ssh/config file.  Changed sshd_config to

[COLOR="SeaGreen"]# X11 tunneling options
X11Forwarding yes
X11DisplayOffset 10[/COLOR]

Still get a error when I try a test x app:

[COLOR="SeaGreen"]pahto% xclock&
[1] 14813
pahto% Error: Can't open display: 

[1]    Exit 1               xclock
[/COLOR]

To keep it simple, I also upgraded to Ubuntu 9.04 late yesterday. Still get the error message.  

This Solaris host has long been able to send X stuff to Windows PCs running Hummingbird X or Reflextion X.

---

### Post by apmcd47 on 2009-05-14
Okay, assuming pahto is the name of your Sun and you have the same username on both machines, please do the following on the ubuntu box:

Start a new terminal or or terminal-tab, then type

```

ssh -X -vvv pahto

```And when you get the prompt on pahto:
```
echo $DISPLAY
exit
```
then upload the terminal contents here.

Andrew

---

### Post by PaulHuffman on 2009-05-18
paul@pauleseries:~$ ssh -X -vvv paul@pahto
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/paul/.ssh/config
debug1: Applying options for *                           
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to pahto [161.217.10.13] port 22.     
debug1: Connection established.                          
debug1: identity file /home/paul/.ssh/identity type -1   
debug1: identity file /home/paul/.ssh/id_rsa type -1     
debug1: identity file /home/paul/.ssh/id_dsa type -1     
debug1: Remote protocol version 2.0, remote software version Sun_SSH_1.0.1
debug1: match: Sun_SSH_1.0.1 pat Sun_SSH_1.0*                             
debug1: Enabling compatibility mode for protocol 2.0                      
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1        
debug2: fd 3 setting O_NONBLOCK                                           
debug1: SSH2_MSG_KEXINIT sent                                             
debug1: SSH2_MSG_KEXINIT received                                         
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                                                                                             
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                                                                 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                              
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                              
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                                                                                  
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                                                                                                  
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                                                                      
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                                                                      
debug2: kex_parse_kexinit:                                                                                                 
debug2: kex_parse_kexinit:                                                                                                 
debug2: kex_parse_kexinit: first_kex_follows 0                                                                             
debug2: kex_parse_kexinit: reserved 0                                                                                      
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1                                                                      
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                                                                 
debug2: kex_parse_kexinit: aes128-cbc,blowfish-cbc,3des-cbc                                                                
debug2: kex_parse_kexinit: aes128-cbc,blowfish-cbc,3des-cbc                                                                
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5                                                                              
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5                                                                              
debug2: kex_parse_kexinit: none,zlib                                                                                       
debug2: kex_parse_kexinit: none,zlib                                                                                       
debug2: kex_parse_kexinit: \377\377\377\377,geo,lcttab,iso_8859_13,iso_8859_15,iso_8859_2,iso_8859_5,iso_8859_7,iso_8859_9,hi_IN.UTF-8,en_AU,en_AU.ISO8859-1,en_NZ,en_NZ.ISO8859-1,es,es_CR,es_CR.ISO8859-1,es_GT,es_GT.ISO8859-1,es_NI,es_NI.ISO8859-1,es_PA,es_PA.ISO8859-1,es_SV,es_SV.ISO8859-1,cz,cs_CZ,cs_CZ.ISO8859-2,de,de.ISO8859-15,de_AT,de_AT.ISO8859-1,de_AT.ISO8859-15,de_AT.ISO8859-15@euro,de_CH,de_CH.ISO8859-1,de_DE,de_DE.ISO8859-1,de_DE.ISO8859-15,de_DE.ISO8859-15@euro,de_DE.UTF-8,de_DE.UTF-8@euro,fr,fr_CH,fr_CH.ISO8859-1,hu,hu_HU,hu_HU.ISO8859-2,pl,pl.UTF-8,et,pl_PL,pl_PL.ISO8859-2,pl_PL.UTF-8,sk_SK,sk_SK.ISO8859-2,bg_BG,bg_BG.ISO8859-5,et_EE,et_EE.ISO8859-15,hr_HR,hr_HR.ISO8859-2,lt,lt_LT,lt_LT.ISO8859-13,lv,lv_LV,lv_LV.ISO8859-13,mk_MK,mk_MK.ISO8859-5,nr,ro_RO,ru,iso_8859_1,ro_RO.ISO8859-2,ru_RU,de.UTF-8,de.UTF-8@euro,ru.UTF-8,ru.koi8-r,ru_RU.ANSI1251,ru_RU.ISO8859-5,es.UTF-8,es.UTF-8@euro,ru_RU.KOI8-R,fr.UTF-8,fr.UTF-8@euro,ru_RU.UTF-8,sh_BA,sr_SP,it.UTF-8,it.UTF-8@euro,sh_BA.ISO8859-2@bosnia,sl_SI,sdebug2: kex_parse_kexinit: \377\377\377\377,geo,lcttab,iso_8859_13,iso_8859_15,iso_8859_2,iso_8859_5,iso_8859_7,iso_8859_9,hi_IN.UTF-8,en_AU,en_AU.ISO8859-1,en_NZ,en_NZ.ISO8859-1,es,es_CR,es_CR.ISO8859-1,es_GT,es_GT.ISO8859-1,es_NI,es_NI.ISO8859-1,es_PA,es_PA.ISO8859-1,es_SV,es_SV.ISO8859-1,cz,cs_CZ,cs_CZ.ISO8859-2,de,de.ISO8859-15,de_AT,de_AT.ISO8859-1,de_AT.ISO8859-15,de_AT.ISO8859-15@euro,de_CH,de_CH.ISO8859-1,de_DE,de_DE.ISO8859-1,de_DE.ISO8859-15,de_DE.ISO8859-15@euro,de_DE.UTF-8,de_DE.UTF-8@euro,fr,fr_CH,fr_CH.ISO8859-1,hu,hu_HU,hu_HU.ISO8859-2,pl,pl.UTF-8,et,pl_PL,pl_PL.ISO8859-2,pl_PL.UTF-8,sk_SK,sk_SK.ISO8859-2,bg_BG,bg_BG.ISO8859-5,et_EE,et_EE.ISO8859-15,hr_HR,hr_HR.ISO8859-2,lt,lt_LT,lt_LT.ISO8859-13,lv,lv_LV,lv_LV.ISO8859-13,mk_MK,mk_MK.ISO8859-5,nr,ro_RO,ru,iso_8859_1,ro_RO.ISO8859-2,ru_RU,de.UTF-8,de.UTF-8@euro,ru.UTF-8,ru.koi8-r,ru_RU.ANSI1251,ru_RU.ISO8859-5,es.UTF-8,es.UTF-8@euro,ru_RU.KOI8-R,fr.UTF-8,fr.UTF-8@euro,ru_RU.UTF-8,sh_BA,sr_SP,it.UTF-8,it.UTF-8@euro,sh_BA.ISO8859-2@bosnia,sl_SI,sdebug2: kex_parse_kexinit: first_kex_follows 0                                                                                                                          
debug2: kex_parse_kexinit: reserved 0                                                                                      
debug2: mac_setup: found hmac-md5                                                                                          
debug1: kex: server->client aes128-cbc hmac-md5 none                                                                       
debug2: mac_setup: found hmac-md5                                                                                          
debug1: kex: client->server aes128-cbc hmac-md5 none                                                                       
debug2: dh_gen_key: priv key bits set: 138/256                                                                             
debug2: bits set: 537/1024                                                                                                 
debug1: sending SSH2_MSG_KEXDH_INIT                                                                                        
debug1: expecting SSH2_MSG_KEXDH_REPLY                                                                                     
debug3: check_host_in_hostfile: filename /home/paul/.ssh/known_hosts                                                       
debug3: check_host_in_hostfile: match line 2                                                                               
debug3: check_host_in_hostfile: filename /home/paul/.ssh/known_hosts                                                       
debug3: check_host_in_hostfile: match line 1                                                                               
debug1: Host 'pahto' is known and matches the RSA host key.                                                                
debug1: Found key in /home/paul/.ssh/known_hosts:2                                                                         
debug2: bits set: 498/1024                                                                                                 
debug1: ssh_rsa_verify: signature correct                                                                                  
debug2: kex_derive_keys                                                                                                    
debug2: set_newkeys: mode 1                                                                                                
debug1: SSH2_MSG_NEWKEYS sent                                                                                              
debug1: expecting SSH2_MSG_NEWKEYS                                                                                         
debug2: set_newkeys: mode 0                                                                                                
debug1: SSH2_MSG_NEWKEYS received                                                                                          
debug1: SSH2_MSG_SERVICE_REQUEST sent                                                                                      
debug2: service_accept: ssh-userauth                                                                                       
debug1: SSH2_MSG_SERVICE_ACCEPT received                                                                                   
debug2: key: /home/paul/.ssh/identity ((nil))                                                                              
debug2: key: /home/paul/.ssh/id_rsa ((nil))                                                                                
debug2: key: /home/paul/.ssh/id_dsa ((nil))                                                                                
debug1: Authentications that can continue: publickey,password                                                              
debug3: start over, passed a different list publickey,password                                                             
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password                              
debug3: authmethod_lookup publickey                                                                                        
debug3: remaining preferred: keyboard-interactive,password                                                                 
debug3: authmethod_is_enabled publickey                                                                                    
debug1: Next authentication method: publickey                                                                              
debug1: Trying private key: /home/paul/.ssh/identity                                                                       
debug3: no such identity: /home/paul/.ssh/identity                                                                         
debug1: Trying private key: /home/paul/.ssh/id_rsa                                                                         
debug3: no such identity: /home/paul/.ssh/id_rsa                                                                           
debug1: Trying private key: /home/paul/.ssh/id_dsa                                                                         
debug3: no such identity: /home/paul/.ssh/id_dsa                                                                           
debug2: we did not send a packet, disable method                                                                           
debug3: authmethod_lookup password                                                                                         
debug3: remaining preferred: ,password                                                                                     
debug3: authmethod_is_enabled password                                                                                     
debug1: Next authentication method: password                                                                               
paul@pahto's password:                                                                                                     
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)                                                             
debug2: we sent a password packet, wait for reply                                                                          
debug1: Authentication succeeded (password).                                                                               
debug1: channel 0: new [client-session]                                                                                    
debug3: ssh_session2_open: channel_new: 0                                                                                  
debug2: channel 0: send open                                                                                               
debug1: Entering interactive session.                                                                                      
debug2: callback start                                                                                                     
debug2: x11_get_proto: /usr/bin/X11/xauth  list :0.0 2>/dev/null                                                           
debug1: Requesting X11 forwarding with authentication spoofing.                                                            
debug2: channel 0: request x11-req confirm 0                                                                               
debug2: client_session2_setup: id 0                                                                                        
debug2: channel 0: request pty-req confirm 1                                                                               
debug3: tty_make_modes: ospeed 38400                                                                                       
debug3: tty_make_modes: ispeed 38400                                                                                       
debug1: Sending environment.                                                                                               
debug3: Ignored env ORBIT_SOCKETDIR                                                                                        
debug3: Ignored env SSH_AGENT_PID                                                                                          
debug3: Ignored env GPG_AGENT_INFO                                                                                         
debug3: Ignored env TERM                                                                                                   
debug3: Ignored env DESKTOP_STARTUP_ID                                                                                     
debug3: Ignored env SHELL                                                                                                  
debug3: Ignored env XDG_SESSION_COOKIE                                                                                     
debug3: Ignored env KONSOLE_DBUS_SERVICE                                                                                   
debug3: Ignored env GTK_RC_FILES                                                                                           
debug3: Ignored env WINDOWID                                                                                               
debug3: Ignored env GTK_MODULES                                                                                            
debug3: Ignored env USER                                                                                                   
debug3: Ignored env LS_COLORS                                                                                              
debug3: Ignored env GNOME_KEYRING_SOCKET                                                                                   
debug3: Ignored env SSH_AUTH_SOCK                                                                                          
debug3: Ignored env SESSION_MANAGER                                                                                        
debug3: Ignored env USERNAME                                                                                               
debug3: Ignored env PATH                                                                                                   
debug3: Ignored env DESKTOP_SESSION                                                                                        
debug3: Ignored env GDM_XSERVER_LOCATION                                                                                   
debug3: Ignored env PWD                                                                                                    
debug1: Sending env LANG = en_US.UTF-8                                                                                     
debug2: channel 0: request env confirm 0                                                                                   
debug3: Ignored env GDM_LANG                                                                                               
debug3: Ignored env KONSOLE_DBUS_SESSION                                                                                   
debug3: Ignored env GDMSESSION                                                                                             
debug3: Ignored env HISTCONTROL                                                                                            
debug3: Ignored env SHLVL                                                                                                  
debug3: Ignored env COLORFGBG                                                                                              
debug3: Ignored env HOME                                                                                                   
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env PROFILEHOME
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 16384
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 32768
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Last login: Mon May 18 10:45:16 2009 from pauleseries
Sun Microsystems Inc.   SunOS 5.9       Generic May 2002
You have new mail.
pahto% echo $DISPLAY
DISPLAY: Undefined variable
pahto% setenv|grep DISPLAY
pahto%

---

### Post by apmcd47 on 2009-05-20
Something is definitely weird here. I can't see a reason for it. And there is no *unset DISPLAY* command in your .login or .cshrc file?

Well, I didn't want to do this, but as tunnelling is not working, try this:

On the Ubuntu box: ```
xauth nextract myauth $DISPLAY
``` where *myauth* is the name of a file to contain the local X authentication info.

Copy the file over to the Sun.

On the Sun: Explicitly set the display, then merge the X authentication file into the Sun's xauth file:```
setenv DISPLAY pauleseries:0
xauth nmerge myauth $DISPLAY
```

You may need to do this every time you start a new session on the Ubuntu box, but not necessarily every time you log onto the Sun.

I honestly cannot see what is wrong here. The debugging info looks the same on my system, which means it should be working on yours. I would say using ssh tunnelling is the best method for X11. I think something is explicitly unsetting DISPLAY, but the above should work as a workaround. I think it is what you wanted in the first place, but in my opinion is fiddly and prone to error. I hope it works, and maybe someone else will know what is going on.

Andrew

---

### Post by PaulHuffman on 2009-05-27
Still doesn't work.  pauleseries is in the Solaris server's host file, but it didn't work to also setenv DISPLAY to the Ubuntu PC's IP address. 

pahto% setenv DISPLAY pauleseries:0
pahto% xauth nmerge myauth $DISPLAY
xauth: (argv):1:  nmerge:  unable to open file pauleseries:0
pahto% xclock &
[1] 9238
pahto% Error: Can't open display: pauleseries:0

---

### Post by apmcd47 on 2009-05-29
> **PaulHuffman said:**
> Still doesn't work.  pauleseries is in the Solaris server's host file, but it didn't work to also setenv DISPLAY to the Ubuntu PC's IP address. 

pahto% setenv DISPLAY pauleseries:0
pahto% xauth nmerge myauth $DISPLAY
xauth: (argv):1:  nmerge:  unable to open file pauleseries:0
pahto% xclock &
[1] 9238
pahto% Error: Can't open display: pauleseries:0

Okay, my mistake. ```
xauth nmerge myauth
```No $DISPLAY in the xauth nmerge command.

Andrew

---

### Post by PaulHuffman on 2009-05-29
I didn't get an error message after the xauth command this time but it still didn't work:

```
paul@pauleseries:~$ ssh -X paul@pahto
paul@pahto's password:
Last login: Fri May 29 10:46:25 2009 from pauleseries
Sun Microsystems Inc.   SunOS 5.9       Generic May 2002
You have new mail.
pahto% setenv DISPLAY pauleseries:0
pahto% xauth nmerge myauth
pahto% xclock &
[1] 24027
pahto% Error: Can't open display: pauleseries:0

```

---

### Post by apmcd47 on 2009-05-30
Sorry, I give up. I cannot see what is wrong at all.

Anybody else want to have a go?

Andrew

---

