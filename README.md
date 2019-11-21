# Zabbix-MSSQL-2008-2016

This has been tested on Zabbix Agent 3.4.6 on Windows Servers 2008/R2,2010,and 2012. With MSSQL versions 2008-2016.

## on the MSSQL machines:

### Assuming:

* PoSh syntax
* Zabbix agent install directory: `$env:ZABBIX_AGENT_DIR = "C:\Program Files\Zabbix Agent"`
* Zabbix agent config fle: `$env:ZABBIX_AGENT_CONFIG = $env:ZABBIX_AGENT_DIR + "\conf\zabbix_agentd.conf"`

### Do as follows:

1. Stop Zabbix Agent service.
1. Copy the contents of the "files" directory into `$env:ZABBIX_AGENT_DIR\conf`
1. Edit `$env:ZABBIX_AGENT_CONFIG` as follows:
    * `Timeout=30`
    * `ServerActive=(IP of Zabbix server)`
    * `Include=c:\Program Files\Zabbix Agent\conf.d\*`
    * `UnsafeUserParameters=1`
1. Start zabbix agent service.

## on the Zabbix Web interface:

1. Import the right template for your Zabbix Server:
    * for Zabbix 3.x, import: `Template App MSSQL 2008-2016.z3.xml`
    * for Zabbix 4.x, import: `Template App MSSQL 2008-2016.z4.xml`
1. Attach template to the relevant MSSQL hosts


**Note:** Only a few triggers have been created but there are over 70 items per database being monitored so you can customise your thresholds as you see fit.

