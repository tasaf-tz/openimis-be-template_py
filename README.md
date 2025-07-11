
# 🧩 Setting Up the `target` Module in the OpenIMIS Backend

This guide provides step-by-step instructions for creating and registering a new Django module named `target` in the OpenIMIS backend (`openimis-be_py`).

---

## 📁 1. Create the `target` Module Directory

Ensure your new module is placed **adjacent to other backend modules**. The `-p` flag ensures that parent directories are created if they don't exist:

```bash
mkdir -p ./openimis-be-target_py/target
```

Your backend directory structure should now resemble:

```
openimis-be_py/
openimis-be-claim_py/
openimis-be-asset_py/
openimis-be-target_py/
```

---

## 🧾 2. Scaffold Required Metadata Files

In the root of `openimis-be-target_py`, create the following files:

- `.gitignore`
- `LICENSE.md`
- `GNU AFFERO GENERAL PUBLIC LICENSE.md`
- `MANIFEST.in`

### Example `.gitignore`

```gitignore
# Virtual environments
**/venv
**/.env

# Python cache and build artifacts
**/__pycache__/
*.py[cod]
*.egg-info
build/
dist/

# IDE and editor settings
**/.idea/
.idea/**
**/.vscode/

# Compiled translation files
**/*.mo

# Locale init
locale/__init__.py
```

This setup helps keep your Git repository clean and focused on source code.

---

## ⚙️ 3. Generate the Django App

Navigate to the main backend Django project directory:

```bash
cd openimis-be_py/openIMIS
```

Then create the Django app inside your new module directory:

```bash
python manage.py startapp target ../../openimis-be-target_py/target
```

> The last argument specifies the directory where the app files will be created.

---

## 🧩 4. Create `setup.py` for the Module

In the root of `openimis-be-target_py`, add a `setup.py` file to define your package metadata:

```python
from setuptools import setup, find_packages

setup(
    name="openimis-be-target_py",
    version="1.0.0",
    packages=find_packages(),
    include_package_data=True,
)
```

---

## 🌐 5. Create `urls.py` for the App

In the app directory `openimis-be-target_py/target/`, create a `urls.py` file with a basic route structure:

```python
urlpatterns = []
```

> You can extend this file later with actual endpoints as your module grows.

---

## 🧪 6. Install the Module Locally via Pip

Install the module in **editable mode** to allow immediate reflection of code changes during development:

```bash
pip install -e ../../openimis-be-target_py/
```

---

## 🧭 7. Register the Module in `openimis.json`

Add your new module to the OpenIMIS configuration file located at `/openimis-be_py/openimis.json`.

Extend the `"modules"` array like this:

```json
{
  "modules": [
    {
      "name": "core",
      "pip": "git+https://github.com/openimis/openimis-be-core_py.git@develop#egg=openimis-be-core"
    },
    {
      "name": "asset",
      "pip": "openimis-be-asset_py"
    },
    {
      "name": "target",
      "pip": "openimis-be-target_py"
    }
  ]
}
```

> Make sure the `"name"` matches the directory name and Python package.

---

✅ Your `target` module is now fully scaffolded, installed, and registered in the OpenIMIS backend. You can now proceed to implement models, views, serializers, and integrations.
