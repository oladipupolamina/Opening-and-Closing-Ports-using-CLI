# Port Listening & Testing on macOS (CLI)

A simple guide to **open**, **test**, and **close** ports using Terminal (macOS).  
*For educational purposes only — do not test systems you don't own or have permission to use.*

---

## Steps Overview

| Step | Purpose | Command | Where |
|------|---------|---------|------|
|  Check current listening ports | Confirm what services are already using ports | `sudo lsof -i -P -n \| grep LISTEN` | Any terminal |
|  Open a port (start listening) | Tell Netcat to listen on port 8000 | `nc -l 8000` | Terminal **Window 1** — keep running |
|  Verify port usage | Check that port 8000 is active and owned by `nc` | `sudo lsof -i -P -n \| grep 8000` | Any terminal |
|  Test connection | Connect to the listening port as a client | `nc 127.0.0.1 8000` | Terminal **Window 2** |
|  Confirm data flow | Type a message in **either** window → it appears in the other | *(just type)* | Both terminals |
|  Close the port | Stop listening and free the port | Press **CTRL + C** | Terminal running `nc` |
|  Recheck | Confirm that the port is fully closed | `sudo lsof -i -P -n \| grep 8000` | Any terminal |

---

## What You Learned

| Action | Meaning |
|--------|--------|
| Listening on a port | Opening a door and waiting for someone |
| Connecting to the port | Someone knocking and entering through that door |
| Exchanging messages | Communication flowing through the door |
| Closing the port | Shutting the door — no more access |

---

## Change the Port Anytime

Replace **8000** with any port number you wish to test:

```sh
nc -l 9000
nc 127.0.0.1 9000
