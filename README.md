# PoC — Inventory Scanner

Een minimalistisch proof-of-concept om snel een Ansible-gebaseerde inventory-scanner uit te rollen in een virtuele test­omgeving.

---

## Inhoudsopgave
1. [Wat je krijgt](#wat-je-krijgt)  
2. [Randvoorwaarden](#randvoorwaarden)  
3. [Installatie](#installatie)  
4. [Gebruik](#gebruik)  
5. [Opschonen](#opschonen)  


---

## Wat je krijgt
- **Vagrant-omgeving** met één *controller*-VM om Ansible-playbooks uit te voeren.  
- **Kant-en-klare Ansible-playbook** voor het scannen & configureren van targets.  
- **Self-contained repo**: geen externe dependencies buiten Vagrant/VirtualBox.

---

## Randvoorwaarden
| Component  | Getest met | Opmerking                           |
|------------|------------|-------------------------------------|
| Git        | ≥ 2.30     | Om de repo te klonen               |
| Vagrant    | ≥ 2.4      | VM-beheer                          |
| VirtualBox | ≥ 7.0      | Provider voor Vagrant              |
| Host-RAM   | 8 GB+      | 2 GB toegewezen aan de controller  |

> **Tip:** Alle andere software (Ansible, Python, etc.) wordt binnen de VM zelf afgehandeld.

---

## Installatie
```bash
# 1. Repo ophalen
git clone https://github.com/sudojelle/Bachelorproef

# 2. VM’s opstarten in de PoC map
vagrant up
```
Het `vagrant up`-commando:
- downloadt het basis-box-image (alleen eerste keer),
- configureert netwerk & SSH,
- provisiont de *controller*-VM.

---

## Gebruik
1. **Inloggen op de controller:**
   ```bash
   vagrant ssh controller
   ```

2. **Playbook draaien vanuit de VM:**
   ```bash
   cd /vagrant/ansible
   ansible-playbook -i inventory.yml config-inventory-scanner.yml
   ```

3. **Resultaten checken:**
   - Output verschijnt realtime in de terminal.
     
---

## Opschonen
Wil je alles weer weggooien?
```bash
vagrant destroy -f
```




