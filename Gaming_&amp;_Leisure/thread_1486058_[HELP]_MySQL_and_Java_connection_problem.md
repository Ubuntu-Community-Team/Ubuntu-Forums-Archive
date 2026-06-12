---
title: "[HELP] MySQL and Java connection problem"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by ex4life6pro on 2010-05-17
i'm new to ubuntu, and wanted to try to run a maplestory private server on it.
i'm succesfully running one on my windows pc,
but now on ubuntu i've some problems!!

i'll show you

```

Could not locate the JDBC mysql driver.
Could not create a SQL Connection object. Please make sure you've correctly configured db.properties.
java.lang.NullPointerException
    at tools.DatabaseConnection$ThreadLocalConnection.get(DatabaseConnection.java:72)
    at tools.DatabaseConnection$ThreadLocalConnection.get(DatabaseConnection.java:44)
    at tools.DatabaseConnection.getConnection(DatabaseConnection.java:36)
    at net.world.WorldRegistryImpl.<init>(WorldRegistryImpl.java:74)
    at net.world.WorldRegistryImpl.getInstance(WorldRegistryImpl.java:89)
    at net.world.WorldServer.main(WorldServer.java:61)



```that's the error i get

i installed my mysql, mysql > java connector driver and i've installed java ofcourse 

this is my connection file

```

package tools;

import constants.ServerConstants;
import java.sql.*;


public class DatabaseConnection {
    private static ThreadLocal<Connection> con = new ThreadLocalConnection();
    private static boolean initialized = true;

    public static Connection getConnection() {
        if (!initialized) {
            throw new IllegalStateException("DatabaseConnection not initialized");
        }
        return con.get();
    }

    public static void release() throws SQLException {
        con.get().close();
        con.remove();
    }

    private static class ThreadLocalConnection extends ThreadLocal<Connection> {
        static {
            try {
              Class.forName("com.mysql.jdbc.Driver");
            } catch (ClassNotFoundException e) {
                System.out.println("Could not locate the JDBC mysql driver.");
            }
        }

        @Override
        protected Connection initialValue() {
            return getConnection();
        }

        private Connection getConnection() {
            DriverManager.setLoginTimeout(15); // Throw an exception after waiting 15 seconds for a connection.
            try {
                return DriverManager.getConnection(ServerConstants.DATABASE_URL, ServerConstants.DATABASE_USER, ServerConstants.DATABASE_PASS);
            } catch (SQLException sql) {
                System.out.println("Could not create a SQL Connection object. Please make sure you've correctly configured db.properties.");
                return null;
            }
        }

        @Override
        public Connection get() {
            Connection con = super.get();
            try {
                if (!con.isClosed()) {
                    return con;
                }
            } catch (SQLException sql) {
                // Munch munch, we'll get a new connection. :)
            }
            con = getConnection();
            super.set(con);
            return con;
        }
    }
}

```and this is my db.properties file 
(it's needed for connection to mysql for maplestory private servers)
```

driver=com.mysql.jdbc.Driver 
url=jdbc:mysql://localhost:3306/bubblesdev 
user = root 
password = root

```so, if you need any more information please ask
and please help me 
i really don't know what to do anymore!!!
and my server needs it reallyy fast!!!!! 
coz my antivirus screwed up my server -_-' (in windows)
(i've also read somewhere that i have to set the right java paths in linux but i have no idea where, what, or who?, so if you think that's the problem please help me with that then)

so from me and all my players
PLEASE HELP FAST!

---

