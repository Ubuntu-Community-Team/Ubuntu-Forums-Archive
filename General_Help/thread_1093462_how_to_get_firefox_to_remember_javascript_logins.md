---
title: "how to get firefox to remember javascript logins?"
date: 2009-03-11
forum: General Help
---

### Post by elitenoobboy on 2009-03-11
I know that there exists a javascript bookmark that can turn autocomplete on so that login info can be stored for sites such as yahoo mail, but what about sites that use javascript to display the login boxes and info? Is there any way, workaround, or extension that will allow me to get around this and store my login credentials?

Example site: [UNM]("https://my.unm.edu/cp/home/displaylogin")

---

### Post by theozzlives on 2009-03-11
FireFox should just ask if you want to store your password information.

---

### Post by nikgare on 2009-03-11
Sxipper add on might help

---

### Post by elitenoobboy on 2009-03-11
The Sxipper popup comes up, but it seems to leave out the username, and I get a login failed message.

Trying to load the site without JS just makes the box go away completely, which doesn't help. 
The problem seems to be the "input type="hidden"" part?
```
<form name="cplogin" action="https://my.unm.edu/cp/home/login" onSubmit="login(); return false;" method="post">
                                                <tr>
                                                  <td align="right"><span class="text10"><B>Password:</B></span></td>
                                                  <td>
                                                        <span class="text10">
                                                          <script language="JavaScript1.2">
                                                          document.writeln("<input class=\"textform\" type=\"password\" name=\"pass\" size=\"" + size + "\" tabindex=2 onFocus=\"hadFocus(true);\">");
                                                          </script><input type="hidden" name="user" value="">
                                                        </span>

                                                  </td>
                                                </tr>
                                          </form>
                                          <tr><td align="center" colspan="2"><a href="javascript:login();" onMouseover="window.status=''; return true;"><img src="/cps/images/btns/login.gif" title="Login" border="0" vspace="5" hspace="3" width="77" height="18" tabindex="3" onLoad="clearCache()"></a><a href="javascript:doCancel();" onMouseover="window.status=''; return true;"><img src="/cps/images/btns/cancel.gif" title="Cancel" border="0" vspace="5" hspace="3" width="62" height="18" tabindex="4"></a></td></tr>
                

```

---

