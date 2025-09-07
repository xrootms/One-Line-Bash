#  10 Bash One-Liners to Make DevOps Life Easier 

## 1️⃣ Find out which process is using most Memory 

```bash
ps aux --sort=-%mem | head -n 10
```
**ps aux** : List all processes with memory & CPU usage.  
**--sort=-%mem** : sorts by memory usage (highest first).  
**head -n 10**: show top 10 processes.

---

## 2️⃣ Monitor CPU Usage in Real-Time 

```bash
top -b -n 1 | grep "Cpu(s)"
```
**top -b -n 1** : runs ‘top’ once, prints the output as plain text.  
**grep "Cpu(s)"** : extracts CPU usage details.

---

## 3️⃣ Check Disk Space Usage

```bash
df -h | awk '$5+0 > 80 {print}'
```
**df -h** : displays disk usage in a readable format.  
**awk '$5+0 > 80 {print}'** : extracts rows where usage exceeds 80%.  
Modify the threshold (80) based on your needs.

---

## 4️⃣ Find Large Files Eating Up Space 

```bash
find / -type f -exec du -h {} + | sort -rh | head -10
```
**find / -type f** : searches for all files.  
**du -h** : calculates file sizes in human-readable format.  
**sort -rh** : Sorts results in descending order.  
**head -10** : limits output to the top 10 largest files.

---

## 5️⃣ Monitor log files in real-time, filtering for error messages 

```bash
tail -f /var/log/syslog | grep --line-buffered "error"
```
**tail -f** : follows the log file as new entries are added.  
**grep --line-buffered "error"** : filters lines containing “error”.

---

## 6️⃣ List all Running Services 

```bash
systemctl list-units --type=service --state=running
```
Shows all currently running services.

---

## 7️⃣ Find and Delete Old Log Files 

```bash
find /var/log -name "*.log" -mtime +7 -exec rm -f {} +
```
**-mtime +7** : selects files older than 7 days.  
🗑**-exec rm -f {} +** : deletes them.

---

## 8️⃣ Download a File in the Background 

```bash
nohup wget -q https://example.com/bigfile.zip &
```
**nohup** : ensures the process runs even after logging out.  
**wget -q** : downloads the file quietly.  
**&** : runs the process in the background.

---

## 9️⃣ Test If a Port is Open on a Remote Server 

```bash
nc -zv example.com 443
```
**-z** : scan mode (don’t send data).  
**-v** : verbose (show output).

---

## 🔟 List All Running Docker Containers 

```bash
docker ps --format "{{.ID}} {{.Image}} {{.Status}}"
```
**docker ps** : lists running containers.  
**--format** : structures the output for better readability.
