# Cursor
## 🧹 How to Fix Frozen Cursor Projects (Clear Chat History Only)

If a project in [Cursor](https://www.cursor.sh) freezes due to long assistant chats or overloaded memory, you can safely reset its workspace data without affecting your code.

This guide helps you:

1. 🔍 Locate the Cursor workspace folder tied to your project
2. 🧼 Delete just that folder to remove chat history and context
3. ✅ Reopen the project cleanly in Cursor

---

### 📁 Step 1: Open the `workspaceStorage` Folder

```bash
cd ~/Library/Application\ Support/cursor/User/workspaceStorage/
```

### 🔍 Step 2: Search for Your Project Folder Name
Replace your-folder-name with the actual folder name of your project (e.g. c1a1, sales-tool-server, etc.)

```bash
grep -r "your-folder-name" ~/Library/Application\ Support/cursor/User/workspaceStorage/*/workspace.json
```

✅ This will return a path like:

```bash
/Users/your-name/Library/Application Support/cursor/User/workspaceStorage/<workspace-id>/workspace.json:  "folder": "file:///Users/your-name/repos/your-folder-name"
```
Copy the "workspace-id" from that result.

### 🗑️ Step 3: Delete the Workspace Folder
This deletes only the Cursor session data for that project. Your actual code is untouched.

```bash
rm -rf ~/Library/Application\ Support/cursor/User/workspaceStorage/<workspace-id>
```

### 🔁 Step 4: Reopen Cursor
```bash
open -a Cursor
```

Then manually open your project folder again.

It will now load as a clean session — no AI chat history, no freeze.

### 🧠 Optional: Disable AI Sidebar Auto-Restore
To avoid future freezes:

Go to Cursor Settings > Cursor Assistant

Turn off:

- "Auto context injection"

- "Restore previous chat"


